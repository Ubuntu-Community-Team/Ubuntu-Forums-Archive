---
title: "Cant create mysql database"
date: 2009-04-01
forum: Server Platforms
---

### Post by rado3105 on 2009-04-01
Hi I want to create database for cacti, I installed mysql-server on ubuntu.

and it shows me this error:
r-c@rclr-srv:~$ sudo mysql -uroot -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
r-c@rclr-srv:~$ mysql -uroot -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
r-c@rclr-srv:~$ 

Can you help how to solve it?

---

### Post by edpatterson on 2009-04-01
> **rado3105 said:**
> Hi I want to create database for cacti, I installed mysql-server on ubuntu.

and it shows me this error:
r-c@rclr-srv:~$ sudo mysql -uroot -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
r-c@rclr-srv:~$ mysql -uroot -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
r-c@rclr-srv:~$ 

Can you help how to solve it?

Try simply mysql -u root -p

then enter the password you assigned the root user when you installed it. It being MySQL not Ubuntu.

---

