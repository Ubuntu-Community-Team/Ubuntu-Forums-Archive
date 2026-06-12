---
title: "I can't connect to mysql from vista host with sun virtualBox."
date: 2009-06-01
forum: Server Platforms
---

### Post by hoboy on 2009-06-01
I am using window vista host and ubuntu 9.04 server runing in sun virtualBox.
I can access tomcat by pointing my brownser to [http://server:808](http://server:808),
but when I [http://server/phpmydadmin](http://server/phpmydadmin) I get the following error
Sorry, the page you were looking for could not be found.
I cann ssh to the server from the host.
I have tried 
mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
But the following command works.
 mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 35
Server version: 5.0.75-0ubuntu10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

---

### Post by eth1 on 2009-06-01
Is the phpmyadmin directory inside the DocumentRoot directory ? 

 [http://server/phpmydadmin](http://server/phpmydadmin) 

or is there an Alias to redirect /phpmyadmin to a directory on the file system ? 

Check your DocumentRoot and see if the directory phpmyadmin is inside it. If not, then move the directory inside and access using the same URL. 

As for the MySQL issue, are you trying to access the MySQL database from a remote/different computer ? Have you allowed the MySQL user with the IP address of the remote/different computer ?

---

