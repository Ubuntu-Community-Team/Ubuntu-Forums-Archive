---
title: "I got a ubuntu server 14.04 with a mysql problem [2002] SQLSTATE[HY000] [2002] Can't"
date: 2015-10-13
forum: Server Platforms
---

### Post by casper8 on 2015-10-13
Hi all,

I know this may vary well be a mysql problem but i desperatly need some help..

I have a owncloud 14.04 server running mysql and owncloud.

the problem is from time to time, maybe about every 10 min, the owncloud login page shows this error

[2002] SQLSTATE[HY000] [2002] Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

this only lasy maybe 10 seconds and than i can login in again. About 10 min after i get the error again... 

Does ANYONE know what the problem could be

---

### Post by slickymaster on 2015-10-13
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by casper8 on 2015-10-13
oops.. sorry!!!!! and thanks for moving it

---

### Post by antonza on 2015-10-14
> **casper8 said:**
> Hi all,

I know this may vary well be a mysql problem but i desperatly need some help..

I have a owncloud 14.04 server running mysql and owncloud.

the problem is from time to time, maybe about every 10 min, the owncloud login page shows this error

[2002] SQLSTATE[HY000] [2002] Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

this only lasy maybe 10 seconds and than i can login in again. About 10 min after i get the error again... 

Does ANYONE know what the problem could be

Can you paste /etc/mysql/my.cnf?

---

