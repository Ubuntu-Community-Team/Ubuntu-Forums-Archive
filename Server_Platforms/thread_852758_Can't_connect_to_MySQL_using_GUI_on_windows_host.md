---
title: "Can't connect to MySQL using GUI on windows host"
date: 2008-07-07
forum: Server Platforms
---

### Post by Griffyn on 2008-07-07
Hi all,

I've got a well-working LAMP ubuntu server 7.10 (command line only) with mediawiki.  I want to have a GUI for MySQL, so I installed the GUI admin tools on a windows XP box and told it the IP address of my ubuntu server.  Won't connect.  It can ping, and of course I can access the web server, but the GUI tool refuses.

The GUI says "MySQL Error Number 2003" after a few seconds of trying.

Help?

---

### Post by windependence on 2008-07-08
The default from mysql server is to be binding to localhost (127.0.0.1), this means it will only accept connections from local applications. 
To change that, edit /etc/mysql/my.cnf and comment out the line bind-address = 127.0.0.1: 
Then you will need to restart the mysql server with: 
/etc/init.d/mysql restart 

Otherwise, here are all the possibilities:

[http://forge.mysql.com/wiki/Error2003-CantConnectToMySQLServer](http://forge.mysql.com/wiki/Error2003-CantConnectToMySQLServer)


-Tim

---

### Post by Griffyn on 2008-07-08
that worked great.  thank you.

---

