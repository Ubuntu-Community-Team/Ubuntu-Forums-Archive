---
title: "How to install Zoneminder-1.36.0-focal1, on UBUNTU 20.04 LTS ( Focal Fossa) Using a D"
date: 2021-05-16
forum: Tutorials
---

### Post by bkjaya1952 on 2021-05-16
In this tutorial ,we are going to use [&#8220;Docker: Enterprise Container Platform&#8221;]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwjRx93Lsc7fAhXILY8KHar-AAcQFjAAegQIAhAB&url=https%3A%2F%2Fwww.docker.io%2F&usg=AOvVaw0Vr113vt10kRWhG_4dy1nX")  ([docker.io]("https://launchpad.net/ubuntu/+source/docker.io")) on Ubuntu 20.04 LTS ( Focal Fossa)
    First
    [B]
Installation of Docker on Ubuntu 20.04 LTS ( Focal Fossa )
[/B]
    
On the Ubuntu terminal

    
```
sudo apt install docker.io
```        **zoneminder-1.34 ,docker images with php 7.4 ,Mysql 8 & MSMTP**

        This image has been created on ubuntu:focal with zoneminder-1.36.0-focal1
    
To pull the Repository from the Docker Hub please refer the following link

    [URL="https://hub.docker.com/repository/docker/bkjaya1952/docker-zoneminder-php7.4-mysql8"]
https://hub.docker.com/repository/docker/bkjaya1952/docker-zoneminder-php7.4-mysql8[/URL]

    
**Usage :**

    
To create a zoneminder-1.34 docker container (name zm)with php 7.4 ,mysql 8 & msmtp

    
On the Ubuntu terminal enter the following commands

        

```
sudo docker create -t -p 8080:80 --name zm --privileged=true -e TZ=Asia/Colombo bkjaya1952/docker-zoneminder-php7.4-mysql8:latest
```    

Note:- Replace Asia/Colombo with your Time Zone

    

```
sudo docker start zm
```        
(You will have to configure the running zm container for mysql 8 ,zm  data base and make some changes to start apache and zoneminder during  the first run .)

    

```
sudo docker exec -t -i zm /bin/bash
```    

(Now you will be with in the zm container. Make changes as follows)
    
**Configuring Mysql **

    
```
updatemysql.sh
   
exit

sudo docker restart zm
```

    [URL="http://localhost:8080/zm/"]
http://localhost:8080/zm/[/URL]

    
(To use msmtp for emailing please refer [https://bkjaya.wordpress.com/2020/12/24/how-to-install-the-latest-zoneminder-master-latest-on-ubuntu-20-04-using-a-docker-image/](https://bkjaya.wordpress.com/2020/12/24/how-to-install-the-latest-zoneminder-master-latest-on-ubuntu-20-04-using-a-docker-image/))

    **Note:- If you want your docker container zm to detect ip camera  automatically, you will have to use the following command when creating  the container .**

    

```
sudo docker create -t -p 80:80 --name zm --network=host --privileged=true -e TZ=Asia/Colombo bkjaya1952/docker-zoneminder-php7.4-mysql8:latest
```    

In this case you will have to restrain in using the port 80 in your host for any other purpose when running the zm container.

    
Then the zoneminder web panel will be at [http://localhost/zm/](http://localhost/zm/)

         [[IMG]https://bkjaya.files.wordpress.com/2021/05/screenshot-from-2021-05-15-16-55-18.png?w=700[/IMG]]("https://bkjaya.files.wordpress.com/2021/05/screenshot-from-2021-05-15-16-55-18.png") 
Figure:- ZM Console after adding USB Cameara

---

