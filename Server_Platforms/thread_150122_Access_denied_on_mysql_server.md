---
title: "Access denied on mysql server"
date: 2006-03-25
forum: Server Platforms
---

### Post by simon_is_learning on 2006-03-25
I started to use mysql on a windows machine, and I am now planning to move over to a linux enviroment. I tried a while ago but I failed then to. And I belive it something really simple, I just can't figure it out.

I have downloaded mysql-server, mysql-admin, mysql-client and so on.
I followed this WIKI: 
[https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=ApachePHPMySQL](https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=ApachePHPMySQL)
And i followed this step also:
cd /usr
sudo ./bin/mysql_install_db --user=mysql

I don't know what it did but..

when I try to connect to mysql I write
mysql -u root -p 
and gets the following error message:
Access denied for user: 'root@localhost' (Using password: YES)

And I can't think of anywhere where I would have changed my root password. 
The same thing happens when I connect with my ubuntu user-name

what have I missed and where can I set the root pass. 
Or have I screwed up so that I have to uninstall it all and start over?

---

### Post by Matt Yun on 2006-03-25
I had a MySQL root access issue as well; this chapter in the MySQL Manual helped:

[Causes of Access Denied Errors]("http://sunsite.mff.cuni.cz/MIRRORS/ftp.mysql.com/doc/en/Access_denied.html")

---

### Post by rich on 2006-03-26
You've installed mysql with a username of "mysql"

try 
mysql -u mysql -p

and see what happens....



Rich

---

### Post by maulattu on 2006-03-26
with the default installation, mysql root user has an empty password.
try this:

mysql --user=root

---

