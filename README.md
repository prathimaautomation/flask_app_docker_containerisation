# Containerise the itjobswatch python app

## Create a `requirements.txt` file with the application dependencies
```
flask
flask_wtf
passlib
requests
pandas==1.3.2
flask_table
list_function
lxml
```

## Create a `Dockerfile` inside the app folder to automate the process of installing dependencies and copying the application into the container
```
FROM python:3.8

WORKDIR	usr/src/app

COPY requirements.txt requirements.txt

RUN pip3 install -r requirements.txt

COPY . .

EXPOSE 5000

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]
```  

## Build the docker image
`docker build -t pjoginipelly/itjobswatch-app .`

## Run the docker image to make sure it is running
`docker run -d -p 5000:5000 pjoginipelly/itjobswatch-app`

## Push the docker image onto the DockerHub
`docker push pjoginipelly/itjobswatch-app`

## Share the app docker image from the DockerHub
`docker pull pjoginipelly/itjobswatch-app`