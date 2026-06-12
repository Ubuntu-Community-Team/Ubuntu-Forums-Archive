---
title: "Mysql connection problem with php"
date: 2022-10-16
forum: Server Platforms
---

### Post by stijnc2 on 2022-10-16
[]("https://askubuntu.com/posts/1435479/timeline")  
          
                                        I'm trying to install a new lamp test system on ubuntu 22.04, but I'm  having troubles with php 8 connecting to the mysql database.


 It displays an connection denied error on all scripts I use. However the  strange thing is that phpmyadmin works with the same login credentials.


 The error I get: Access to database is denied for databasenameremoved: SQLSTATE[HY000] [2002] (trying to connect via (null))


 This happens for multiple (all) database users. I'm sure that the username and password are correct. I also tried the root account, but is has the same problem.

Does anybody know how to fix this?


 Thanks,
Stijn

---

### Post by LHammonds on 2022-10-17
Did you create this PHP application or are you trying to get someone else's app to work?  Maybe it is not yet compatible with PHP8.  Also, make sure you are using the right connection parameters such as port.

The biggest slowdown for migrating from my 20.04 servers to 22.04 is waiting on app compatibility.  If it is a really old app, it might be trying to use mysql drivers instead of mysqli.

If you are trying to connect from a different machine, you will need to adjust the firewall rules and unbind the service to just localhost.

LHammonds

---

### Post by stijnc2 on 2022-11-12
Late response, but I found the problem. PHP for some reason did not know that localhost was local for mysql. I could not get it fixed. But because mysql was always eating cpu I removed it and installed mariadb. Now everything works as it should :).

---

### Post by LHammonds on 2022-11-12
Hehehe, love MariaDB

---

