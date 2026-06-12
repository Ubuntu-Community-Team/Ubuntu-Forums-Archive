---
title: "LAMP stack w Hadoop"
date: 2014-07-19
forum: Server Platforms
---

### Post by Crafty Kisses on 2014-07-19
Hello, so I'm having a bit of issues getting LAMP running for various development projects I'm working on. So I remove the current LAMP stack that I currently have via 
```
apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.5 mysql-common mysql-server mysql-server-5.5 php5-common php5-mysql
```
I also used the purge option when removing "debconf data", now I've used various methods on installing "apache2" in particular this one
```
sudo apt-get install apache2
``` I then restart network ```
sudo /etc/init.d/apache2 restart
```
Apache then gives me this error ```
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
```
So the first obvious thing that comes to mind is to edit the apache config file ```
sudo nano /etc/apache2/apache2.conf
``` I then added the following line to the config file ```
ServerName localhost
``` I then deactivated the old site, and activated the new one. Using I believe "a2dissite" ```
$ sudo a2dissite 000-default && sudo a2ensite mysite
``` I then go on to install PHP, etc etc ```
libapache2-mod-php5
``` The issue is here, Apache is not actually parsing the php after I restarted it, I installed "libapache2-mod-php5". It's not the corrupt php5 packet either, I've done research. Surprisingly MySQL installed just fine by using ```
mysql-server libapache2-mod-auth-mysql php5-mysql
``` Any ideas would be really helpful, thanks fellow Linux users!

---

