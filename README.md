# Vacation Database

Created with Postgres, Nginx, Flask + Gunicorn. Includes front-end to test some functionality. Make sure you have Docker before running. Handles concurrent API calls with Flask-SqlAlchemy's Scoped Session and Gunicorn's threaded workers.

### Routes:
* `/` for registration page
* `/cancel/<uid>` to cancel by unique registration id
* `/modify/<uid>/<mmddyy>/<mmddyy>` to modify registration arrival and departure dates

### Setup:
1. `make bootstrap-db` to initialize Postgres tables
2. `make all` to run the rest of the containers (nginx, flask app)
3. `localhost:8080` to test the app

### To Clear Database:
1. `make refresh-db`
2. `docker kill $(docker ps -aq)`
3. `make bootstrap-db`

### Testing:
* `sudo npm install -g loadtest`
* ` loadtest -n 1000 -c 20 -k http://localhost:8080/reserved`
