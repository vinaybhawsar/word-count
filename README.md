# Word Count Flask Application

This project uses flask, Redis and postgresql.


## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. 

### Prerequisites

What things you need to install the software and how to install them

* [Postgres](https://www.postgresql.org/download/)
* [Redis](https://redis.io/download)
* [Python](https://www.python.org/downloads/)

### Installing

A step by step series of examples that tell you how to get a development env running

* Create virtual environment  

```
virtualenv --python python3 venv
```

* Activate the environment

```
source venv/bin/activate
```

* Install python dependencies

```
pip install -r requirements.txt
```

* Add environment variable
```
export APP_SETTINGS="config.DevelopmentConfig"
export DATABASE_URL="postgresql://user:password@localhost/wordcount_dev"
```

* Create database in postgres
```
$ psql
# create database wordcount_dev;
CREATE DATABASE
# \q
```

* Database initialization
```
$ python manage.py db init
  Creating directory /flask-by-example/migrations ... done
  Creating directory /flask-by-example/migrations/versions ... done
  Generating /flask-by-example/migrations/alembic.ini ... done
  Generating /flask-by-example/migrations/env.py ... done
  Generating /flask-by-example/migrations/README ... done
  Generating /flask-by-example/migrations/script.py.mako ... done
  Please edit configuration/connection/logging settings in
  '/flask-by-example/migrations/alembic.ini' before proceeding.
```

* Create migration by running the migrate command
```
$ python manage.py db migrate
  INFO  [alembic.runtime.migration] Context impl PostgresqlImpl.
  INFO  [alembic.runtime.migration] Will assume transactional DDL.
  INFO  [alembic.autogenerate.compare] Detected added table 'results'
    Generating /flask-by-example/migrations/versions/63dba2060f71_.py
    ... done
```

* Apply the upgrades to the database using the db upgrade command
```
$ python manage.py db upgrade
  INFO  [alembic.runtime.migration] Context impl PostgresqlImpl.
  INFO  [alembic.runtime.migration] Will assume transactional DDL.
  INFO  [alembic.runtime.migration] Running upgrade  -> 63dba2060f71, empty message
```

* Start Server
```
python manage.py runserver
```

* Start Redis Worker
```
python worker.py
```
