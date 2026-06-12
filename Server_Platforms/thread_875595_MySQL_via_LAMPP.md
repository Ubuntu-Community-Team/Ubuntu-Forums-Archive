---
title: "MySQL via LAMPP"
date: 2008-07-31
forum: Server Platforms
---

### Post by Tsarj on 2008-07-31
I get Error 2002 when trying to start the MySQL via lampp. 
```
/opt/lampp/lampp start
Starting XAMPP for Linux 1.6.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

/opt/lampp/bin/mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/opt/lampp/var/mysql/mysql.sock' (2)
```

It doesn't create it. Not sure if the daemon even creates the sock file... Anyone?

---

### Post by Tsarj on 2008-07-31
Bump

---

### Post by jhyland87 on 2008-07-31
Hello D00D!

So You said LAMPP is a multi package installer, those tend to make life hard on a typical server, even if it installs fine, it ties them all together so when something updates, and you try to update it, its very hard, because there are all types of hidden settings and files that you dont install yourself. Installing one by one is usually the best thing to do.

Go to howtoforge.com and search "ubuntu LAMP". You will get a lot of results, however some of those are for the server edition of Ubuntu.


I would remove all of your installed applications, and try this command:
> sudo apt-get install apache2 mysql-server php5 libapache2-mod-php5 php5-xsl php5-gd php-pear libapache2-mod-auth-mysql php5-mysql

That should install everything as administrator..

OR....

system->administration->synaptic package manager

Search for Apache, SQL, and PHP.

any of those should work ;-) :guitar:

---

### Post by jhyland87 on 2008-08-01
Actually sir, I found one that beats all of those!

[http://forum.codecall.net/tutorials-classes-code/5679-setting-up-lamp-server-ubuntu.html](http://forum.codecall.net/tutorials-classes-code/5679-setting-up-lamp-server-ubuntu.html)

---

