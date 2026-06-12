---
title: "Cannot import MySQL database - please help"
date: 2009-04-18
forum: Server Platforms
---

### Post by jamieh on 2009-04-18
I'm moving a site from an Ubuntu server to an OS X server and I'm trying to move the MySQL database. I exported it with the mysqldump command, but when I try to import it to OS X with phpmyadmin, I get the following:

> Error
SQL query:

/*!40103 SET TIME_ZONE='+00:00' */;


MySQL said: 

#1146 - Table 'mysql.time_zone_name' doesn't exist 

Whats wrong with it?

Thanks

---

### Post by Thirtysixway on 2009-04-19
Try removing that line from the mysqldump, then import it and see if it works.

---

