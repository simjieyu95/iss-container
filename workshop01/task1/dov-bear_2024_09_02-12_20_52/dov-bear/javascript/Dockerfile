
# Define the build-time argument with a default value
ARG BUILD_VERSION=22


# Use the ARG in the FROM directive
FROM node:${BUILD_VERSION}
# How to build.

### Create a directory 
WORKDIR /app

### After the line above, we are now inside the /app directory in the VM.
### Copy from the local files to the container/VM's /app directory
COPY main.js .
COPY package.json .
COPY package-lock.json .

### Copy local directories to the container/VM's /app directory.
### Copy the local public directory and paste it in the container/VM's /app directory. 
### Now the container/VM's /app directory has the views folder.
COPY public public
COPY views views 

### Install node modules.
RUN npm ci

# How to run.
### Set the env variable with name APP_PORT.
ENV APP_PORT=3000
ENV INSTANCE_NAME="bear bear"
ENV INSTANCE_HASH="bear hash"
### Set which port to expose. This means that the container opens the port APP_PORT.
EXPOSE ${APP_PORT}

### Run the application. Since we are currently in the /app directory, main needs to be found in the /app directory.
ENTRYPOINT node main 