---
title: "Zoneminder-Docker with Mysql 8 on Ubuntu 19.10"
date: 2020-01-15
forum: Tutorials
---

### Post by bkjaya1952 on 2020-01-15
In this tutorial ,we are going to use [&#8220;Docker: Enterprise Container Platform&#8221;]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwjRx93Lsc7fAhXILY8KHar-AAcQFjAAegQIAhAB&url=https%3A%2F%2Fwww.docker.io%2F&usg=AOvVaw0Vr113vt10kRWhG_4dy1nX")  ([docker.io]("https://launchpad.net/ubuntu/+source/docker.io"))  on Ubuntu 19.10. 

First
 [B]
Installation of Docker on Ubuntu 19.10[/B]
 
On the Ubuntu terminal
 
```
sudo apt install docker.io
```
 
Then use , [bkjaya1952/docker-zoneminder-master-mysql8]("https://hub.docker.com/r/bkjaya1952/docker-zoneminder-master-mysql8")   Docker Repository to make a container . 


[IMG]https://bkjaya.files.wordpress.com/2020/01/screenshot-from-2020-01-14-23-43-41.png?w=700[/IMG]

Figure:- bkjaya1952/docker-zoneminder-master-mysql8:1.33.16 Repository at dockerhub



```
sudo docker create -t -p 8080:80 --shm-size=4096m --name zm --privileged=true bkjaya1952/docker-zoneminder-master-mysql8:latest
 
sudo docker start zm
```

[B]
You will have to configure the running zm container for mysql 8  ,zm  data base and edit the timezone  only for the first run .
[/B]

```
sudo docker exec -t -i zm /bin/bash
```
 
(Now  you will be with in the zm container.
 Make changes as follows)
 
```
mysql -uroot -p < /usr/share/zoneminder/db/zm_create.sql

 
mysql

 
CREATE USER 'zmuser'@localhost IDENTIFIED WITH mysql_native_password BY 'zmpass';

 
GRANT ALL PRIVILEGES ON zm.* TO 'zmuser'@'localhost' WITH GRANT OPTION;

 
FLUSH PRIVILEGES ;

 
quit

 
mysqladmin -uroot -p reload
```

 

```
dpkg-reconfigure tzdata
```

 
Then edit your timezone

 
```
exit
```

 
```
sudo docker restart zm
```

To get zoneminder panel on web browser 
[URL="http://localhost:8080/zm/"]
http://localhost:8080/zm/[/URL]


( The procedure of  composing an image can be obtained from the following links
[https://bkjaya.wordpress.com/2020/01/15/how-to-build-a-zoneminder-master-docker-image-with-mysql-8-msmtp/](https://bkjaya.wordpress.com/2020/01/15/how-to-build-a-zoneminder-master-docker-image-with-mysql-8-msmtp/)  )

---

### Post by bkjaya1952 on 2020-01-23
Today (23- 01- 2020 ), Mr. Isaac Connor has published the  first successful Zoneminder-master-eoan  package for Ubuntu 19.10. in his [website]("https://launchpad.net/~iconnor/+archive/ubuntu/zoneminder-master") .

The Installation procedure is explained in the following web link 


[HOW TO INSTALL ZONEMINDER, v1.34.0. ON UBUNTU 19.10 (eoan), with mysql 8]("https://bkjaya.wordpress.com/2020/01/23/how-to-install-zoneminder-v1-34-0-on-ubuntu-19-10-eoan-with-mysql-8/")

---

### Post by emanueledb on 2020-07-04
muy bueno, me sirven de mucho todos los tutoriales, ya que estoy intentando instalar todo en una maquina

---

