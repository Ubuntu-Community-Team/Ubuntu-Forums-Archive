---
title: "mysql error 1045 and error 1698"
date: 2018-06-06
forum: Server Platforms
---

### Post by icewizard22 on 2018-06-06
I just installed mysql and I've been getting these errors when trying to run mysql. I followed a few directions on stack overflow to fix this, but nothing is working. The first thing I did was use ' sudo mysql -u root -p' and I was able to get into mysql then, and then I tried 'use mysql', then 'update user set plugin='' where User='root';' then 'mysql> flush privileges;' and '/q'. I don't know what this did but it was supposed to fix my error and it didn't. After that I get into mysql again and using sudo to get into was returning a 1045 error. So I followed another stackoverflow solution that didn't fix my problem which was in order on my terminal : 'sudo service mysql stop', then 'sudo mysqld --skip-grant-tables' and with that when trying to get into mysql I got this error 'ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'. Then after getting this error I followed I wrote these into my command line 'sudo apt-get purge mysql-server mysql-client', then 'sudo apt-get install mysql-server mysql-client', and 'sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf' which then changed my terminal to a file in a nano editor and I changed this line on the file the bind address from 127.0.0.1 to localhost. then I entered this 'sudo /etc/init.d/mysql restart' and my terminal showed this [ ok ] Restarting mysql (via systemctl): mysql.service. 

But now when I try to get into mysql it still shows and error 1045 when logging in using this command  mysql -u root -p. I don't know what I'm doing and don't want to break anything so I'd appreciate any help with this.

---

### Post by LHammonds on 2018-06-07
#1 - Check to make sure you did not run out of space.

#2 - If I were you, I'd uninstall mysql and purge the configuration files from the system.  Then re-install it.

I do not know how you installed MySQL in the 1st place but I would recommend using MariaDB instead.  You can check my signature for a link on the steps I use to create a database server.

LHammonds

---

