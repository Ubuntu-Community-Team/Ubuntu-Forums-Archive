---
title: "HOWTO: Install Apache2, MySQL5, PHP5 (Screencast)"
date: 2007-12-26
forum: Server Platforms
---

### Post by Josh1 on 2007-12-26
I have created a screencast on how to install Apache2, MySQL5, PHP5 on Ubuntu.
This tutorial should work with all versions of Ubuntu.

The commands I did were:
```
sudo apt-get install apache2
sudo apt-get install php5
sudo /usr/sbin/apache2 -k restart
sudo chown josh /var/www
sudo apt-get install mysql-server
mysql -u root -p
sudo apt-get install php5-mysql
```

I've currently only uploaded it in a .GIF format, soon I will be uploading it into a .SWF format, but it is 20mb.

I've tried to go a little slow so you can see what is happening.

[CENTER][SIZE="4"][View Screencast.[]("http://joshuataylor.info/apache2mysql5php5_install.php")/SIZE][/CENTER]

Enjoy,
Josh

---

### Post by K.Mandla on 2007-12-26
Moved to Servers and Security.

---

