---
title: "Ubuntu mySQL guide"
date: 2006-04-01
forum: Server Platforms
---

### Post by amitroy5 on 2006-04-01
Does anyone know of a mySQL guide for Ubuntu that will help install the program and do tasks like configuring phpmyadmin and mysqlcc? Thanks!

---

### Post by dermotti on 2006-04-01
Can't you just install phpmyadmin via synaptic?

---

### Post by amitroy5 on 2006-04-01
Yes you can. But it is hard configuring it. I am looking for a guide to guide me through properly configuring mySQL.

---

### Post by adamkane on 2006-04-01
Apache/MySQL/PHP install guide:
[https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP")

phpmyadmin works fine with mysql4/php4, and is the easiest tool to use. If you have mysql4.1 or mysql5, you have to install phpmyadmin from source.

---

### Post by amitroy5 on 2006-04-01
Thanks. However, I still cannot set a root password for some reason. I always get an error. How do you set it? Thanks!

---

### Post by adamkane on 2006-04-01
What are you using to change the password?

Terminal? mysql-administrator? phpmyadmin?

---

### Post by amitroy5 on 2006-04-01
Sorry, via the terminal, I entered this:

sudo mysqladmin -u root password mypassword here

Howerver, I get this error:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

---

### Post by gruepig on 2006-04-02
Sounds like mysqld isn't running.  Check with 'ps aux | grep msyql' and/or '/etc/init.d/mysql status'.  If it isn't running, start it by typing 'sudo /etc/init.d/mysql start'.

If there's a mysql process running, check that the daemon is listening with 'sudo lsof -i | grep mysql'.  Then make sure you can establish a connection to the mysql port.  Try 'telnet localhost 3306'.  (If you connect, exit out of the telnet session with control-].)  If mysql is running, but you can't connect to it, check the config file: /etc/mysql/my.cnf.

---

### Post by amitroy5 on 2006-04-02
Thanks for the suggestion! I tried telnet, and it did this:

amit@Server:~$ telnet localhost 3306
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
NHost 'localhost.localdomain' is not allowed to connect to this MySQL serverConnection closed by foreign host.
amit@Server:~$

I am looking though the config file. I am not sure what to change though. I can confirm that mySQL is running, however.

---

### Post by s7eam on 2006-04-03
Can you login on your mysql server without passowrd?
**mysql -u root -p**
Don't enter any password just press **Enter**

Now when you're logged in create a password for the root:
**mysql> SET PASSWORD FOR root@localhost=PASSWORD('yourpass');**

---

### Post by Abhi Kalyan on 2006-11-04
> **s7eam said:**
> Can you login on your mysql server without passowrd?
**mysql -u root -p**
Don't enter any password just press **Enter**

Now when you're logged in create a password for the root:
**mysql> SET PASSWORD FOR root@localhost=PASSWORD('yourpass');**
MY GOD!
Guys i had a major time out with the proper syntax GRHHH!!!
exactly as i typed it atlast, does every comma and space matter so much, GRHHH!

SET Password = PASSWORD( 'sathyam' );

this i typed after logging into the mysql,
after loads of trying i found that me being so dumb had set my password to
"newrootsqlpassword"
Please laugh

Thank you guys You are wonderful
Love you all

---

