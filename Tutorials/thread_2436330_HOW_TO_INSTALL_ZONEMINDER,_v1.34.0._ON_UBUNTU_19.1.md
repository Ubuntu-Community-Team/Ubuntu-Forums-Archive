---
title: "HOW TO INSTALL ZONEMINDER, v1.34.0. ON UBUNTU 19.10 (eoan), with php 7.4 &amp; mysql 8"
date: 2020-02-04
forum: Tutorials
---

### Post by bkjaya1952 on 2020-02-04
At the moment PHP mysqli connector does not have support for  caching_sha2_password. We will have to use mysql_native_password until  the PHP 7.4 is revised to support caching_sha2_password.[B]

Installation of[/B] [B]php 7.4

[/B]```
sudo su 

apt install -y software-properties-common 

add-apt-repository ppa:ndrej/php

apt update

apt -y install php7.4
```

[B][B][B][B][B][B]Installation of Zoneminder 

To install Zoneminder Please refer [URL="https://launchpad.net/~iconnor/+archive/ubuntu/zoneminder-master"]Connor&#8217;s web site

[/URL][/B][/B][/B][/B][/B][/B]```
sudo add-apt-repository ppa:iconnor/zoneminder-master

sudo apt-get update

sudo apt install zoneminder

rm /etc/mysql/my.cnf

cp /etc/mysql/mysql.conf.d/mysqld.cnf /etc/mysql/my.cnf 

sed -i "15i default_authentication_plugin= mysql_native_password" /etc/mysql/my.cnf

/etc/init.d/mysql start
  
mysql

CREATE USER 'zmuser'@localhost IDENTIFIED WITH mysql_native_password BY 'zmpass'; 

GRANT ALL PRIVILEGES ON zm.* TO 'zmuser'@'localhost' WITH GRANT OPTION;

FLUSH PRIVILEGES ;

quit

mysqladmin -uroot -p reload

chmod 740 /etc/zm/zm.conf 

chown root:www-data /etc/zm/zm.conf

adduser www-data video 

a2enmod cgi 

a2enconf zoneminder 

a2enmod rewrite

chown -R www-data:www-data /usr/share/zoneminder/ 

systemctl enable zoneminder

service zoneminder start

service apache2 reload
```

Open zoneminder web console ([http://localhost/zm/](http://localhost/zm/))

Note:-If you want to install docker-zonemider ,please refer the following link 

[bkjaya1952/docker-zoneminder-master-php7.4-mysql8]("https://hub.docker.com/r/bkjaya1952/docker-zoneminder-master-php7.4-mysql8")
 
If you get an error message on timezone in logs , you will have to enter the timezone in /etc/php/7.4/apache2/php.ini

---

### Post by David_Camp on 2020-02-15
> [COLOR=#000000]If you get an error message on timezone in logs , you will have to enter the timezone in /etc/php/7.4/apache2/php.ini[/COLOR]

I'm new with Ubuntu. Can you tell me more about this?

---

