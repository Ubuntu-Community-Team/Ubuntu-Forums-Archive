---
title: "Connecting to MySQL externally"
date: 2007-07-19
forum: Server Platforms
---

### Post by numberboy on 2007-07-19
Hey,
I'm having a problem with a home LAMP server (running Ubuntu Server 7.04). It's got MySQL installed, but it won't allow anyone other than localhost to talk to it. If I try to connect to the server from inside my home network using MySQL Administrator I get an error message stating that "Host '192.168.1.11' is not allowed to connect to this MySQL server". The machine itself it connected to the network fine; Apache allows connections without issue. Furthermore, I can access the server though SSH (so I've setup the root user/password properly).

I believe this is an issue of MySQL only allowing one IP (that being localhost, I presume, since setting bind-address to 192.168.1.11 temporarily stopped MySQL from starting) access, so I've tried various things. I commented out the bind-address line in /etc/mysql/my.cnf and that hasn't stopped the error; I set the bound address to 0.0.0.0 and that hasn't stopped it, and I set the address to 192.168.1.11 (the Windows XP machine I'm trying to connect from) which stopped MySQL from starting after a restart.

All that I want to do is be able to connect from my Windows development machine using MySQL Administrator so I can have a GUI for database management. Is this possible?

Thanks

---

### Post by foxylad on 2007-07-19
I switched to Postgres a while ago, but from memory Mysql limits where you can connect from in the mysql database user table. By which I mean a database called "mysql". Once you are logged on, try "USE mysql;" and ""SELECT * FROM users". GRANT stores it's settings in this database.

Also try "GRANT ALL ON *.* TO remuser@% IDENTIFIED BY "password" WITH GRANT OPTION;" 

That should grant full access to all databases/tables (*.*) to user remuser from all addresses (...@%). Be careful if your database is available on the internet though, make sure you use good passwords.

---

### Post by z600 on 2007-08-08
Hey,

I'm having the same problem. I have done the following:

1. updated the my.conf file's bind address to 0.0.0.0. 
2. I have also added a user that can connect from anyhost to the mysql user tables as well as a user that connects from the specific machine I am connecting from. 
3. I have also tried it with disabling both firewalls  (the connecting machine and the mysql machine). 

None of this works. If I use telnet to connect to the mysql instance I get a "connection refused" message. Any ideas? if I do a netstat on the mysql box it is listening on 3306 for 0.0.0.0.  It almost sounds like a firewall issue. I'm using firestarter to start/stop the firewall.

I have installed mysql before on windows with no problems and have been able to share it out of the box.

---

### Post by z600 on 2007-08-21
Sorry guys! My fault. I was connecting to the wrong IP. Everything works now! :)

---

