# Apache Airflow and Apache Cassandra

This repository contains the Airflow DAG that extract news data from a Live API data. The extracted data is processed and the data is loaded into Apache Cassandra database. We have used the Airflow-cassandra provider to load our data into the Cassandra database. 

We have provided two different scripts that help to install Airflow using Docker container and using the Python PIP, you can just start the bash scripts using `./airflow_pip_installer.sh`.

The CQL script for our database setup is in the file execute.cql. You can use automation to copy this file into the Cassandra docker container and create your databases using Airflow as the orchestrator.

With that, let's setup Airflow on the docker container. 
### Clone the repo
```
git clone https://github.com/yTek01/example-cassandra-and-apache-airflow.git
```
### Build the Airflow image with additional dependencies
```
docker build . -f Dockerfile --tag <ImageName>
```
### Start, and run the containers with the command below
```
docker-compose -f docker-compose.Airflow.yaml -f docker-compose.Cassandra.yaml up -d
```
### Start the bash script to install Airflow CLI
```
./airflow.sh
```

### Go into your Cassandra database and create your database and the table schema. 
```
docker exec -it example-cassandra-and-apache-airflow-cassandra-1 cqlsh
```

* Go into the execute.cql file and use the CQL script to create database and your table schema

### Confirm that Airflow is running [localhost:8080](http://localhost:8080/)
Now navigate to the DAGs page and run the Airflow_and_Cassandra DAG, start building your own DAG. 

