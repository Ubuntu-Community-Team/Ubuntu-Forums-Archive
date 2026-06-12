---
title: "Mysql Error"
date: 2010-06-17
forum: Server Platforms
---

### Post by samyverse on 2010-06-17
HI All,
  
   I have installed Mysql in Ubuntu 9, for the use of roundcube database.After installing iam getting the error like this 

* Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
  

So because of this in the roundcube configuration its giving the error message that MYSQL is not installed. So Kindly give me a idea how to solve this.

Regards
SAMY

---

### Post by spynappels on 2010-06-17
That message is telling you that MySQL is working correctly, it always checks for tables which were not closed cleanly. The problem might lie with the credentials Roundcube is using to connect to MySQL?

---

