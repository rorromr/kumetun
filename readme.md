# jirafa
Jira based maintenance and spare management

## Docker
Install docker and docker-compose
```
https://docs.docker.com/compose/install/
```

## Python setup
```
pyenv install 3.6.6
pyenv virtualenv 3.6.6 jirafa
pip install --upgrade pip
pip install atlassian-python-api
```

## Postgres setup
```
docker-compose up
```
### SQL
```
CREATE DATABASE jirafa
  WITH OWNER = postgres
       ENCODING = 'UTF8'
       TABLESPACE = pg_default
       LC_COLLATE = 'en_US.utf8'
       LC_CTYPE = 'en_US.utf8'
       CONNECTION LIMIT = -1;

CREATE TABLE spares(
  code VARCHAR(30) PRIMARY KEY NOT NULL,
  barcode VARCHAR(30) NOT NULL,
  system_id INT NOT NULL,
  subsystem_id INT NOT NULL,
  description TEXT, 
  current_qty DECIMAL NOT NULL,
  min_qty DECIMAL NOT NULL,
  providor_id INT NOT NULL,
  price DOUBLE PRECISION NOT NULL,
  extra_data JSON
);

CREATE TABLE providors(
  id INT PRIMARY KEY NOT NULL,
  name VARCHAR(30) NOT NULL,
  address TEXT,
  phone VARCHAR(12),
  extra_data JSON
);

CREATE TABLE systems(
  id INT PRIMARY KEY NOT NULL,
  parent_id INT,
  name VARCHAR(30) NOT NULL
);
```
