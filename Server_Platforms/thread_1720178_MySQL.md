---
title: "MySQL"
date: 2011-04-02
forum: Server Platforms
---

### Post by doxramos on 2011-04-02
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
I've had this problem to the point where I thought I messed up my actual configuration so bad that I reinstalled Ubuntu to get rid of all the MySQL configuration; I ran MySQL through Windows with a breeze, but I'm getting some errors like that after restarting my computer just a few minutes ago and I have not changed anything in my SQL settings; if someone could help please do. And Keep in mind; new to Ubuntu :)
I'm on Ubuntu 10.10 64 bit and running MySQL 5.1
If you want more detailed configuration let me know how or if you can pull the info up here go to
[http://www.doxramos.dyndns.info/php5;](http://www.doxramos.dyndns.info/php5;) the actual error that I get from Navicat and from the website is at
[http://www.doxramos.dyndns.info](http://www.doxramos.dyndns.info)

Update: 20110402
Connection for controluser as defined in your configuration failed. Just got that when I tried to log in to phpmyadmin as well; not sure if it's related or not. Thank you.

Thank you much.

---

### Post by songshu on 2011-04-03
that does look like a messed up configuration, usually that would be /etc/mysql/my.cnf

```
apt-get delete mysql-server
```
rename the files in /etc/mysql/ like
```
sudo mv /etc/mysql/my.cnf /etc/mysql/my.cnf-original
```
and the other files as well.....
```
sudo apt-get install mysql-server
```

you could also try to create the file its looking for first since it isn't there with
```
sudo touch /var/run/mysqld/mysqld.sock
```

---

### Post by doxramos on 2011-04-03
Tried all above to no avail. :( I double checked and the mysqld.sock file is there, this is just frustrating.

---

### Post by BkkBonanza on 2011-04-03
I don't think you want to run touch to create a file there. Since this is a socket the presence of the file may prevent the socket from being created. You should make sure that mysql has permissions to create the socket in that directory. Usually it would but it sounds like something is preventing mysql from opening the socket there.

Make sure the socket is deleted when mysql server is down before starting. (Not the directory, just the socket in the directory, should be gone when mysql not up, and maybe if it still exists due to some previous crash it could prevent re-opening.)

Also, check with **netstat -l** that the unix socket is listed.

---

### Post by doxramos on 2011-04-05
So Honestly. I restarted my computer and bam. My SQL server is working again. Not sure what fixed it, but there's nothing for me to troubleshoot if everything is working again....

---

