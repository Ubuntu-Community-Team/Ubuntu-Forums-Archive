---
title: "Install Web Server in Ubuntu"
date: 2011-06-17
forum: Server Platforms
---

### Post by nana72 on 2011-06-17
Maybe  some of you all to know how to make a web server in Ubuntu, but it's  worth posting here because my future, I hope some tutorials to make some  kinds of applications that a web-based ERP, cloud computing etc.. So this thread could be a benchmark, Amiin ...

Ana assume the company is connected to the inet or local repo via cd or LAN.

Open a terminal, install some of these packages:

sudo apt-get install apache2

test whether the web server has been installed properly by opening your browser and type localhost

if the page appears like this, it means your web server is working properly ...



more ...

sudo apt-get install php5

sudo apt-get install mysql-server

sudo apt-get install phpmyadmin

Special  to the mysql installation it asks for username and password root mysql  administrator who'll use it later (user and password up to you, which is  important to remember ya Sob).

whereas  phpmysql package used for the mysql via a web editor so for who are  allergic to sql syntax on the console can gunain this feature. To  access please open your browser type localhost / phpmyadmin enter the  mysql root user and password reply has been made during the installation  mysql Wink

Most of the placement of web files dicemplungin in / var / www or / usr / share. But  many web applications ported to the server root directory so swollen as  a result, ngakalinnya can menggaktifkan user module in the kernel dir. It means I'll be dialihin web content to the user's directory in / home / user / public_html. how ...

sudo a2enmod userdir

then restart your web server by typing dikonsole

sudo / etc/init.d/apache2 restart

make a directory in / home / user / public_html

try a test by opening your browser and type:

[http://localhost/](http://localhost/) ~ user

Do not forget to sign "~" before your user name exp: / localhost / ~ novalnd
if there is no problem, will look like the following picture:




this way you can share applications with other web users who connect to you via the network.

Next, we stayed the implementation of web applications that we want to attach. For web developement can use this feature to view the web in real, if the fix uploaded to hostserver live in inet

good luck

---

