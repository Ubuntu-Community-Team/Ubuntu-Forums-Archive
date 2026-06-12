---
title: "[SOLVED] mysql fails to start"
date: 2008-05-20
forum: Server Platforms
---

### Post by infosys on 2008-05-20
During boot-up MySQL fails to start. I’ve gone through several different forums, and the two main problems I’ve seen posted were: 1. mysql-server was not installed, and I’ve verified mine is. 2. In the /etc/mysql/my.cnf file the bind-address was incorrect, normally due to the IP address of the server changing. I’ve verified mine is set to the loop-back, 127.0.0.1.

When I try to start MySQL manually, by using the command “sudo /etc/init.d/mysql start”, it fails. When I try to start MySQL manually, by using the command “sudo mysql start”, it fails giving “ERROR 2002 (HY000): Can’t connect to local MySQL server through socket ‘/var/run/mysqld/mysqld.sock’ (2)”.

Anybody know what I can do or where I should look?

I’ve had some permissions problems in the past, this could be related to that, but I’ve not been able to find anything.

---

### Post by anystupidname on 2008-05-20
Do /var/log/mysql.err and mysql.log and messages tell us anything useful? :popcorn: It has to be something screwed up in the config or a permission issue like you suggested.

---

### Post by infosys on 2008-05-20
I opened both of those files (mysql.err and mysql.log) with the nano command. Both of these files are empty though.

---

### Post by Wim Sturkenboom on 2008-05-21
There are two parts to mysql:
the server (mysql**[COLOR="Red"]d[/COLOR]**) and the client (mysql)

With your second attempt (*sudo mysql start*), you're trying to start the client, not the server.

I don't run an Ubuntu server, so I don't know if *sudo /etc/init.d/mysql start* is the correct command? You say it fails, so what is the error that you get?

---

### Post by infosys on 2008-05-21
When doing the sudo /etc/init.d/mysql start it goes through what looks like the same process as when the system is booting up. It says "* Starting MySQL database server mysqld" and it waits a few seconds, then to the right of that comes up "[[COLOR="Red"]fail[/COLOR]]".

---

### Post by infosys on 2008-05-21
Turns out it was a permissions problem, and one that suprised me at that. The /var/log/mysql folde was owned by root somehow, but was supposed to be owned by mysql. So, I changed it back, and now it works fine.

---

### Post by jgeewax on 2010-03-25
> **infosys said:**
> Turns out it was a permissions problem, and one that suprised me at that. The /var/log/mysql folde was owned by root somehow, but was supposed to be owned by mysql. So, I changed it back, and now it works fine.

Might also want to check /var/run/mysqld and make sure that's owned by the mysql user. That fixed it for me.

---

### Post by simrob on 2011-09-01
jgeewax, that worked for me as well; I had to create the /var/mysqld directory and make it owned by mysql. and then everything went from near-silently not starting to starting without a problem.

I'd been running mysql without problems for ages at this point, why on earth would this suddenly become a problem?

---

### Post by sp00n82 on 2012-03-28
Kind of a necrothread, but it appeared as one of the top results on google for "ubuntu mysql suddenly fails".
I've had the same problem mentioned here, but for my VirtualBox Ubuntu server 11.04 installation, it was simply running out of available disk space. Clearing the cached package files via "apt-get clean", freeing up some additional space, allowed me to start the mysql daemon just fine again. I couldn't find any log messages pointing to that problem, so basically this was a long shot. But it worked.

---

