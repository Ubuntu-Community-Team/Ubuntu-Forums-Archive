---
title: "change MySQL 5.1.41 to Percona Server 5.5 on ubuntu server 10.04"
date: 2011-10-04
forum: Server Platforms
---

### Post by rs2k on 2011-10-04
I'm using ubuntu 10.04. How would I go about changing from using MySQL 5.1.41-3ubuntu12.10 to Percona Server 5.5?


I simply installed Apache2, PHP5, Phpmyadmin and MySQL by running 

apt-get install apache2
apt-get install php5 libapache2-mod-php5
apt-get install mysql-server
apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin


How would I go about replacing MySQL with Percona Server 5.5?
If I apt-get remove mysql-server then apt-get install percona-server-server-5.5, what will that do to my databases and phpmyadmin?

Having to reinstall everything is no problem, I just want to do it with minimal downtime.

---

### Post by Captain James T Kirk on 2012-03-19
Pretty old question which was unanswered but I will update it for those looking for this answer (can not stand when no one updates).

All files and everything are interchangeable with what I have done that is similar. Percona database is a fork of MySQL and is a basic drop-in replacement for the most part. 

Hope it worked out for you.

---

### Post by rs2k on 2012-03-19
Percona is running great!

Here's my install log from my server.

::Percona DB Install::
gpg --keyserver  hkp://keys.gnupg.net --recv-keys 1C4CBDCDCD2EFD2A
gpg -a --export CD2EFD2A | sudo apt-key add -

nano /etc/apt/sources.list
	add:
		deb [http://repo.percona.com/apt](http://repo.percona.com/apt) lucid main
		deb-src [http://repo.percona.com/apt](http://repo.percona.com/apt) lucid main


apt-get update
apt-get install percona-server-server-5.5
/etc/init.d/apache2 restart
::Percona DB Install::

---

