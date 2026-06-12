---
title: "How To install Php 5.2.1"
date: 2007-04-18
forum: Server Platforms
---

### Post by b-rabbit on 2007-04-18
Hi everybody, it's veru good to be a part of this forum...well I've been using ubuntu about 2 months, obvious i'm not an expert :(:(jeje,...I want to know more about web servers and stuff like that, I have installed Apache 2.2.4 and now I want to install Php 5.2.1 but I don't know how to make it as a part of Apache, I did this on windows and it's easy but I'm newbie on linux so, if someone could help me I will thank a lot...or tell me some link where I can refer to...Thanks once again and i'll be waiting for your responses

---

### Post by az on 2007-04-18
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

and then set a mysql root password and off you go...

---

### Post by PhragMunkee on 2007-04-18
To set the MySQL password, do:

mysqladmin -u root password yournewpassword

Obviously, replace "yournewpassword" with the password you want to use for the root user for the MySQL server.  It is typically a good idea to have this different from any other root passwords.

---

