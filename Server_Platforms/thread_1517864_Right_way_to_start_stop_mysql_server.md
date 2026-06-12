---
title: "Right way to start stop mysql server"
date: 2010-06-25
forum: Server Platforms
---

### Post by lleming on 2010-06-25
I have limited memory so i prefer to start apache and mysql manually only then i really need. I cause of apache its simple /etc/init.d/apache2 start|stop. But with mysql i have a problem first of all:
mysql doesnt like this way /etc/init.d/mysql start|stop
its asking to use sudo sevice mysql start|stop
But this way has one issue. If i will stop and start mysql throw service mysql stop|start then later i dont have access anymore to mysql. I cannon login to mysql.
Another question is why apache starts 5 process 
ps -A | grep apache2
 2993 ?        00:00:00 apache2
 2996 ?        00:00:00 apache2
 2997 ?        00:00:00 apache2
 2998 ?        00:00:00 apache2
 2999 ?        00:00:00 apache2
 3000 ?        00:00:00 apache2

So how should i start and stop my mysql server properly?

---

### Post by Ryan Dwyer on 2010-06-25
Apache starts 5 processes because they are workers. By default it tries to keep five spare.

sudo /etc/init.d/mysql start should be no different from sudo service mysql start (and same with stop). Same with Apache. If you can run /etc/init.d/apache2 start without sudo then you've probably made some modification to your /etc/sudoers file to allow this.

Your query about logging on to MySQL is a bit hard to follow. Can you post your terminal session showing the issue?

---

### Post by lleming on 2010-06-26
generally i found what was the problem. i dont know the reason but mysql on my ubuntu 64 10.04 refuse blank pass 
if i will put 
uleming@Ubuntu-Laptop:~$ sudo dpkg-reconfigure mysql-server-5.1
// i put here blank pass
mysql stop/waiting
mysql start/running, process 9739
uleming@Ubuntu-Laptop:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
uleming@Ubuntu-Laptop:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

but
uleming@Ubuntu-Laptop:~$ sudo dpkg-reconfigure mysql-server-5.1
// put some pass here
mysql stop/waiting
mysql start/running, process 9972
uleming@Ubuntu-Laptop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 34
Server version: 5.1.41-3ubuntu12.3 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

---

### Post by lleming on 2010-06-26
a little bit more 

sudo /etc/init.d/mysql stop
[sudo] password for uleming: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
mysql stop/waiting
uleming@Ubuntu-Laptop:~$ sudo /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
mysql start/running, process 10108
uleming@Ubuntu-Laptop:~$ mysql -u root -p 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 34
Server version: 5.1.41-3ubuntu12.3 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 



SO problem was that mysql  doesnt allow blank pass

---

### Post by Ryan Dwyer on 2010-06-26
It says in dpkg-reconfigure mysql-server-5.1:

> While not mandatory, it is highly recommended that you set a password for the MySQL administrative "root" user.                               

**If this field is left blank, the password will not be changed.**

If you want to remove the password on your MySQL root account, do it using a query rather than through configuring the package.

---

### Post by lleming on 2010-07-03
So problem was solved only particularly. I can connect to mysql only with using pass. Without pass i am not able to connect to mysql at all.
Plus i dont have access to mysql under my own account on server.
I mean 
shell$ mysqladmin ping 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'ule....'@'localhost' (using password: NO)'

I dont know what the problem its really weird.

---

### Post by lleming on 2010-07-03
Eventually i got the answer. Accounts for server and mysql different that was the problem. And if i will try
shell~$ mysql
by default mysql takes login name from my own account which not registred in mysql

---

