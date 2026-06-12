---
title: "mysql trouble"
date: 2007-03-07
forum: Server Platforms
---

### Post by tronica on 2007-03-07
I have a web server setup, and a friend of mine wants to use gallery on my server, i let him set it up, over ssh. well i come home the next day and mysql is completely messed up.

> root@itransfer:~# mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


I can't even log in. I thought he reset my password, but I don't think he did. How can i reset the password? thanks.

---

### Post by tronica on 2007-03-07
nevermind, i figured it out. for anyone thats having the same problem

> $ /etc/init.d/mysql stop
$ mysqld_safe --user=mysql --skip-grant-tables --skip-networking &
$ mysql -u root mysql
mysql> UPDATE user SET Password=PASSWORD('newpassword') where USER='root';
mysql> FLUSH PRIVILEGES;

---

### Post by neilcavendish on 2007-03-07
Hi guys i am having the same problem i have installed MySQL.
and run 

mysqladmin -u root password 'new-password'. 

When i try and log i get 

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

I have tried a lot of ideas that are in posts and none have worked could anyone help, Thanks.

---

