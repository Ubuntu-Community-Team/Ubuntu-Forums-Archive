---
title: "Ubuntu MySQL Setup with mySQL Workbench"
date: 2011-01-04
forum: Server Platforms
---

### Post by francischung on 2011-01-04
Hi All,

I am new to Ubuntu server setup and wish to ask something in regards of Ubuntu LAMP server. 

I had setup a Ubuntu with LAMP Server option and installed phpmyadmin as well.

I need to install mySQL Workbench on my laptop and access to the mySQL in the Ubuntu server that I had setup. I tried to connect to the server but it keep saying unable to reach the mySQL server. I keep getting error like "Can't connect to MySQL server on '192.168.0.30' (111)".  Any advice that I can connect my workbench to the server?

I don't mind the port 3306 is opened as it will not be connected to the internet as long as I can connect the Workbench to mySQL in the server

---

### Post by wongo888 on 2011-01-04
Find your MySQL config file (my.cnf is usually in /etc/mysql) and comment out the following line by putting a hash character in front of it as shown:

```

# bind-address = 127.0.0.1

```

Restart the server:

```

$ sudo service mysql restart

```

See

[http://dev.mysql.com/doc/refman/5.5/en/can-not-connect-to-server.html](http://dev.mysql.com/doc/refman/5.5/en/can-not-connect-to-server.html)

---

