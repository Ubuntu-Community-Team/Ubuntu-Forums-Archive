---
title: "mysql database missing"
date: 2013-03-05
forum: Server Platforms
---

### Post by littlewenwen on 2013-03-05
Dear All

I just installed MySQL Server 5.5 under Ubuntu 12.10 through repository. When I was trying to change the password, I got following message:

```
ll@wenwen:~$ mysqladmin -u root password "newpassword";
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
ll@wenwen:~$
```

I googled online; it seems the reason I could not change password is because the "mysql" database is lost. So I checked the installed database and got following information:

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| test               |
+--------------------+
2 rows in set (0.00 sec)

mysql>
```

So is the "mysql" database missing? How can I recover it?

---

### Post by GordThompson on 2013-03-06
Before you ran the `show databases;` command you must have connected to MySQL. If you did that using the command

```
mysql
```
then you connected to MySQL as the "null" user (no username and no password). In that case the 'mysql' database will not show up because the null user does not have permission to see it.

When installing 'mysql-server' from the repositories you will be prompted to set the MySQL root password. If you repeatedly decline (and it will ask you about three (3) times) then the MySQL root user will have no password. This is not recommended for security reasons. However, if you do that then you can connect to MySQL as root via

```
mysql --user=root
```
If that command gives you the same error you received before ('Access denied for user 'root'@'localhost' (using password: NO)') then your MySQL server *does *have a root password. If you don't know what that password is then you can reset the MySQL root password using the instructions [here]("http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html") (from the MySQL Reference Manual).

---

### Post by littlewenwen on 2013-03-06
Wow! Thank you so much! What you said is EXACTLY what I felt confused about! Now I understand (I think) the difference between different connection mode.

I followed your suggestion; and then tried to connect to mysql using following command:
```
mysql -u root -p
```
It did ask for password (thankfully I still I remember it); after I supplied password, I got connected. Then I issued show databases command, and the 'mysql' showed this time:

```
mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| test               |
+--------------------+
4 rows in set (0.03 sec)

mysql> 
```

Again, thank you very much!

---

