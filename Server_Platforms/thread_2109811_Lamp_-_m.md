---
title: "Lamp - m"
date: 2013-01-28
forum: Server Platforms
---

### Post by Vegan on 2013-01-28
MySQL has been flipped around so much it seems that they are now adversely affecting the LAMP stack

I realize there are other databases out there, so what is the new stack going to be like now?

I have Ubuntu server in a VM along with everything else

---

### Post by Lars Noodén on 2013-01-28
Some distros are moving to MariaDB.  For right now it is more or less a drop-in replacement for MySQL.  Eventually the code base will probably diverge, but for now it is fine.

---

### Post by hydn79 on 2013-01-28
MariaDB has been benchmarked as slower than MySQL 5.5 though:
[http://www.mysqlperformanceblog.com/2012/02/18/mariadb-5-3-4-benchmarks/](http://www.mysqlperformanceblog.com/2012/02/18/mariadb-5-3-4-benchmarks/)
[http://blog.mariadb.org/benchmarking-mariadb-5-3-4/](http://blog.mariadb.org/benchmarking-mariadb-5-3-4/)

---

### Post by Vegan on 2013-01-28
guess that means MySQL while still GNU is going to have to be maintained somehow, and going commercial is not going to help anyone

Apache is now looking for developers for OpenOffice

I use Visual Studio which does not like the popular open source like git etc

I do have the foundation server though so a collaborative effort is not impossible

---

### Post by SeijiSensei on 2013-01-29
I started with PostgreSQL when MySQL was still commercially licensed and have never looked back.  Migration can be a bit tricky, though, because MySQL has some SQL language features that PostgreSQL does not support.  If you're considering moving away from MySQL, install PostgreSQL on your server, then use mysqldump to export your database(s).  Try importing them into PostgreSQL and see what errors pop up.  You might just need to make a few minor edits in some of the SQL code.

---

