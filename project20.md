MIGRATION TO THE CLOUD AND CONTAINERIZATION PART 1: DOCKER AND DOCKER COMPOSE

#### Install Docker and prepare for migration to the Cloud

Installed Docker engine on my Ubuntu server.

    sudo apt-get update

    sudo apt-get install docker-ce docker-ce-cli containerd.io


![docker](images/docker.JPG)


MySQL in container

Pull MySQL Docker image from Docker Hub

    docker pull mysql/mysql-server:latest

![pullmysql](images/pullmysql.JPG)


Run command below to list image downloaded
Deploy the MySQL Container

    docker run -e MYSQL_ROOT_PASSWORD=password1 -d mysql/mysql-server:latest


![runmysql](images/runmysql.JPG)


CONNECTING TO THE MYSQL DOCKER CONTAINER

The MYSQL server container can be connected directly or through another container running MYSQL client.

#### 1st Approach:

Connecting directly to the container running the MySQL server:

    docker exec -it quizzical_chaum mysql -uroot -p


![mysql](images/mysql.JPG)


#### 2nd Approach:

#### Create a network

docker network create --subnet=172.18.0.0/24 tooling_app_network

Create an environment variable to store the root password:

export MYSQL_PW=password1
