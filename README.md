# Using Oracle Official Docker Images on Oracle Container Cloud Service

Oracle and Docker certified official docker images are publish on **[Docker Store](https://store.docker.com/)** from Apr-19-2017. This tutorial describes how to urilize Container Cloud Service with Docker Store and create a WebLogic Server Container on it.

## Requirement

- [Docker Store](https://store.docker.com/) account
- [Oracle Container Cloud Servicre](https://cloud.oracle.com/container) subscription

## Tutorial
### 1. Manage Docker Images on Docker sotre
#### 1.1. Get Docker Images
![](docs/images/dockerstore1.png)

Search images with keyword **"Oracle"** and then select Oracle WebLogic Server. Next click **Get Content**. You can use this docker image.

#### 1.2. Check WebLogic Image
![docker_store_wls](docs/images/ccs-with-dockerstore08.png)

Display **My Content** view from account menu and click **Setup**

![docker_store_uri](docs/images/ccs-with-dockerstore09.png)

You can check docker image name and tag.

### 2. Add Docker Store to Registory
#### 2.1. Login Container Cloud Service Console
![dashboard](docs/images/ccs-with-dockerstore01.png)

At first you login to Containe Cloud Service Console and display Dashboad. Then click **Registries** on the left pane.


#### 2.2. Add Docker Store to Registory
![registory](docs/images/ccs-with-dockerstore02.png)

Click **New Registory** on upper right corner menu.

![add_registory](docs/images/ccs-with-dockerstore03.png)

Input Docker Store Account Information:
- Docker Store URL: **index.docker.io/store**
- Email Address: it is registered on Docker Store
- User Name: Docker Store Account User Name
- Password: Docker Store Account Password

![validate_accont](docs/images/ccs-with-dockerstore04.png)
Click **Validate** and then you can check the account information is correcrt or not. Finally you click **Save** when the account information is valid.

![dockerstore_on_list](docs/images/ccs-with-dockerstore05.png)

You can find the docker store on your list.

#### 3. Define WebLogic Service
Service is the template for making docker container run.

#### 3.1. Display service definition screen
![services](docs/images/ccs-with-dockerstore06.png)

Click **Services** on the left pane and then you can see the service list. You can find **New Service** on the upper right corner and then click it.

#### 3.2. Define new service definition
![docker_image](docs/images/ccs-with-dockerstore07.png)

Input the information needed on Service definition.
- Service Name
- Docker Image (Name and Tag)
- [Option] Parameters which docker run command uses

![](docs/images/ccs-with-dockerstore10.png)
Define port as a parameter. This definitions is port mapping between host environment and container environment.You need to some port when you access some port opened in the container. Port is assigned at random in default though you can configure the port beforehand.

![](docs/images/ccs-with-dockerstore11.png)
**"-p"** option is used with docker run command if you use docker CLI though you can edit on Container Cloud Service.

![](docs/images/ccs-with-dockerstore12.png)
You can find the port mapping definition when you defined with GUI.

### 4. Run WebLogic Container
#### 4.1. Deploy WebLogic Container
![](docs/images/ccs-with-dockerstore13.png)
You can find **WebLogic Service** just defined before. And you can find **Deploy** green button on the left side of it. Click it.

![](docs/images/ccs-with-dockerstore14.png)
Modal windows shows. You just click deploy on the bottom right corner of the window.

![](docs/images/ccs-with-dockerstore15.png)
Just wait for a while. Docker downloads docker image from Docker store by docker pull command.

#### 4.2. Login WebLogic on Container
![](docs/images/ccs-with-dockerstore16.png)
Then you can see the deployment view which shows WebLogic Container runs successfully. Next click the container name to confirm container information.

![](docs/images/ccs-with-dockerstore17.png)
You can see Container specific information view. You can find **View Log** on the view and click it.

![](docs/images/ccs-with-dockerstore18.png)
You can see docker log which WebLogic generates. In the log you can find **admin password**. Admin password is generated automatically and randomly when you create the container for the first time. You use it when you login WebLogic Admin Console or so.

![](docs/images/ccs-with-dockerstore19.png)
Next click host name on Deployment view to check host environment.

![](docs/images/ccs-with-dockerstore20.png)
You can find **Public IP Address**. You use it to access the container.

![](docs/images/ccs-with-dockerstore21.png)
You can access WebLogic Administration Console on Container with the following URL:
- **http://[PUBLIC IP]:7001/cosole**

You use password which you checked in the docker log.

![](docs/images/ccs-with-dockerstore22.png)

Domain is created and run. This domain is very simple which is configured with just admin server only. So you can use this docker image for the base image and cusutomize it.

## Demo

## Licence

Released under the [MIT license](https://gist.githubusercontent.com/shinyay/56e54ee4c0e22db8211e05e70a63247e/raw/44f0f4de510b4f2b918fad3c91e0845104092bff/LICENSE)

## Author

[shinyay](https://github.com/shinyay)
