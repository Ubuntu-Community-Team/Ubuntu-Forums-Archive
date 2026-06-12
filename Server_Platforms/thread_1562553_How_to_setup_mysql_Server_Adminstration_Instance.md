---
title: "How to setup mysql Server Adminstration Instance"
date: 2010-08-27
forum: Server Platforms
---

### Post by jrtboht on 2010-08-27
I've successfully setup a query connection using ssh.  I used the following

Standard TCP/IP
Hostname 127.0.0.1
Port 3306

Simple enough but how to do I setup a connection for Server Administration

If I go to setup a new connection 
-I click on "Take Parameters From Existing Database Connection"
-After that I get all 3 checkmarks in Open Database, Get Server Version and Get Server OS
-I click next and put Ubuntu (mysql package) for select mysql type
-on the next page I get errors for check location of start and stop commands and mysql configuration file (I assume it's checking the machine I'm on and not using the ssh tunnel)

A few more details:
I'm running ubuntu server 10.04.1 and connecting from a windows vista machine that is outside of the network.  I'm using putty for my ssh tunnel.

---

