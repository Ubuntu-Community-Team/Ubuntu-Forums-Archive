---
title: "cannot install mysql OR postgresql"
date: 2006-09-29
forum: Server Platforms
---

### Post by pumpapa on 2006-09-29
When installing mysql, synaptics complains that that requires mysql-client (4.0.24-10ubuntu2.3) which again requires libreadline4. I have libreadline5 installed and can not remove it because just about half of my packages require it.

Postgresql CAN be installed, but when installing php5-pgsql I get:
php5-pgsql:
 Depends: phpapi-20041030
  Depends: php5-common (=5.0.5-2ubuntu1.4) but 5.1.2-1ubuntu3.2 is to be installed


I have no idea how to proceed. Any help would be much appreciated.

--Pum

---

### Post by pumpapa on 2006-09-30
The problem is largely the Synaptic Pacakge Manager which adheres to strict (version based) dependenciess. 

Installing mysql directly from/following [http://dev.mysql.com/doc/refman/5.0/en/installing-source.html](http://dev.mysql.com/doc/refman/5.0/en/installing-source.html) seems to work fine.

---

