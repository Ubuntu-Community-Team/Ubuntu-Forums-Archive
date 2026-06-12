---
title: "MySQL :administer from workstation, how to?"
date: 2008-06-08
forum: Server Platforms
---

### Post by MarioFromBelgium on 2008-06-08
Hi,

I have MySQL on UBUNTU hardy server without gui.
I administer my UBUNTU server from a workstation through ssh with putty
I have no php installed, I have tomcat 6 up and working on this server

How can I best administer MySQL from a workstation?

Mario

---

### Post by alguin2 on 2008-06-08
Install the MySQL Administrator and MySQL Query Browser (either download from mysql.com or install via Synaptic Package Manager.

---

### Post by Monicker on 2008-06-08
It can also be administered from the console with the mysql command.

```
mysql -h server-ip-address -u username -p
```


There are some tasks which are definitely easier in the gui tools, though I generally use the console for simple queries and changes.

---

### Post by hyper_ch on 2008-06-09
no matter how much I like the cli I think administration of mysql server/dbs is very easily done with phpMyAdmin :) although I haven't tried MySQL Administrator or MySQL Query Browser.

---

### Post by MarioFromBelgium on 2008-06-11
Hi,

me again(the one that started this thread) 
I have Msql administrator on my workstation (tha one from work thus...winxp)
When I start the program I get asked som data to connect to.
When I enter the ip-adress of the server that is on my local lan, leave the port-number as it is :3306 and enter as username root and password 
I get : could not connect to the specified instance. Pingen the server is no prob. 

Do I have to change the port-number?

---

### Post by mbeach on 2008-06-11
your server may only be listening to requests from localhost.  

comment out (using the # character) the line
bind-address = 127.0.0.1
in /etc/mysql/my.cnf
restart mysql and see if that makes a difference.

---

### Post by mbeach on 2008-06-11
you may also have to grant some permissions for whichever user you are attempting to connect as, from which your particular host or IP.  I think by default (it used to anyways) grant access within mysql to connect from the local machine.


something like:
grant all privileges on *.* to <userName>@<hostName> identified by 'password' 
see:
[http://dev.mysql.com/doc/refman/5.0/en/privileges.html](http://dev.mysql.com/doc/refman/5.0/en/privileges.html)

---

