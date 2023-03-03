## Run Spark with Hadoop, Docker, and Airflow
On this repo, I will show you how to run Spark with Hadoop, and scheduled the task/DAG in Airflow

## If you want to follow the step, you may require to install follow requirement :
1. Docker Desktop : https://www.docker.com/products/docker-desktop/

## Here are the step to run Spark with Hadoop, and scheduled the task/DAG in Airflow : 
1. Build docker hadoop base. Run `docker build -t hadoop-base:3.3.1 -f Dockerfile-hadoop .` in your VSCode terminal
2. Compose docker hadoop by run `docker-compose -f docker-compose-hadoop.yml up -d`
3. Build docker airflow in airflow directory by run `cd airflow` and `docker build -t airflow-hadoop-base:3.3.1 .`
4. Compose docker airflow hadoop base by run `docker-compose -f docker-compose-airflow.yml up -d`
5. You can check in your Docker Desktop, hadoop base and Airflow already available
6. In Docker Desktop, go to Namenode terminal and create hdfs directory
7. Place the `Sales.csv` file in hdfs directory by run `hadoop fs -put /hadoop-data/input/Sales.csv input/`
8. On VSCode terminal, run `docker ps`. You will find airflow-webserver and link to the localhost
9. Copy the link to your google chrome or mozilla. It will bring you to airflow UI. You can login with username and password `airflow`
10. Add and define new connection `spark-hadoop`
11. Select DAG `avg_product_price` and run DAG by click unpause on the left corner and run play button on the right corner
12. It will show green if the DAG is successfully run 
