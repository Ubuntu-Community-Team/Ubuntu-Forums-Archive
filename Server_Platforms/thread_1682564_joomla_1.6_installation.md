---
title: "joomla 1.6 installation"
date: 2011-02-06
forum: Server Platforms
---

### Post by hirohitosan on 2011-02-06
Hi there. I installed Ub. Server 10.10 - LAMP, postgresql, Mail Server. Now I want to install Joomla 1.6. Sfter starting installation first error: ```
Could not connect to the database. Connector returned number: Unable to connect to the Database: Could not connect to MySQL.

```I don't know where to search for help for moving forward. Thanks!

---

### Post by volkswagner on 2011-02-06
Verify you can log into mysql with root user and also any users you created for joomla.

```
mysql -u root -p
```
Then enter the root password for mysql.

---

### Post by kopial on 2011-02-08
Hey I am also having this same problem. (Trying to install Joomla 1.5 on xampp 1.7.4). I followed the above steps & this is what I get in the terminal:

daniel@daniel-laptop:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Any idea what went wrong? Is there an issue between xampp 1.7.4 with Joomla 1.5? How do I get xampp 1.6 for linux? I can't seem to find that version on apachefriends.org...appreciate your help!!:(

---

### Post by James78 on 2011-02-08
> **kopial said:**
> Hey I am also having this same problem. (Trying to install Joomla 1.5 on xampp 1.7.4). I followed the above steps & this is what I get in the terminal:

daniel@daniel-laptop:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Any idea what went wrong? Is there an issue between xampp 1.7.4 with Joomla 1.5? How do I get xampp 1.6 for linux? I can't seem to find that version on apachefriends.org...appreciate your help!!:(
Why not just install a LAMP stack instead? Much easier..

In short..
```
sudo tasksel
*select LAMP and press enter to install*
```
If tasksel isn't installed, just install it before running the above command.
```
sudo apt-get install tasksel
```

For more information on LAMP...
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by kopial on 2011-02-09
Finally I got through this problem. Remove the Lampp 1.7 then install an older Lampp 1.64 version.

---

### Post by hirohitosan on 2011-02-12
thanks guy's. I installed phpmyadmin set up mysql password and it works. I could install J1.6

---

