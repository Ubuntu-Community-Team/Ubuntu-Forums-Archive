---
title: "[Guide] How to Install Redmine Quickly ( BASIC GUIDE)"
date: 2012-07-29
forum: Tutorials
---

### Post by sharif_aly on 2012-07-29
In easy simple steps and quickly done


After intsall Ubuntu Server

Using Terminal :

1. Update 
```
sudo apt-get update
```2.
```
sudo apt-get upgrade
```3.Install nano

```
sudo apt-get install nano
```Then Select Nano
```
sudo /usr/bin/select-editor

```4. Install MySQL Server

```
sudo apt-get install mysql-server
```5. Install Redmine

```
sudo apt-get install redmine-mysql
``````
sudo apt-get install redmine
``````
apt-get install libapache2-mod-passenger
``````
sudo /etc/init.d/apache2 restart
```In case you want to reconfigure it
```
dpkg-reconfigure -plow redmine
```Do some configuration
```

ln -s /usr/share/redmine/public /var/www/redmine

chown -R www-data:www-data /var/www/redmine
echo "RailsBaseURI /redmine" > /etc/apache2/sites-available/redmine
a2ensite redmine
/etc/init.d/apache2 reload
/etc/init.d/apache2 restart

```Then you can check it on your browser
```
http://[yourwebsite url]/redmine
```

---

### Post by uRock on 2012-07-29
Moved to ***Tutorials & Tips***.

---

### Post by sharif_aly on 2012-07-29
[B][SIZE=3]Thanks uRock for moving the topic.
[/SIZE][/B]

---

### Post by Raafat1991 on 2013-02-02
It works for me...many thanks .

---

