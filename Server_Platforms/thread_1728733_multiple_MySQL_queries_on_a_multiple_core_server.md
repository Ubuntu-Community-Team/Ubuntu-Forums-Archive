---
title: "multiple MySQL queries on a multiple core server"
date: 2011-04-14
forum: Server Platforms
---

### Post by c01e on 2011-04-14
If I have a php script that first connects to a MySQL database, then I run 4 big queries, then close the connection to the MySQL database. Will it put each of the 4 queries on each of the cores (FYI: the server is a quad core).

Or do you have to connect to the MySQL database for each query, to make it use each core for each query?

From my tests, it appears the top method does all the 4 queries on one core. Is there anyway, to tell what queries are running on what core?

---

### Post by elico on 2011-04-14
depends on mysql and not on php.
as long as i know mysql is multithreaded so expect it to be cores utilized.
but it's still depends only on the DB system and structure.
after the php will get the results then you are comming to the problematic place of "will php utilize the cpus? "

---

### Post by c01e on 2011-04-14
Is there anything I can check/set in the MySQL setup to ensure the DB system/structure is multithreaded?

---

### Post by BkkBonanza on 2011-04-14
MySql definitely uses multiple threads and linux will manage them to different cpus on demand. At least I'm pretty sure the linux kernel is effcient this way.

If you run **htop** and select the options screen (F2) you can turn off "hide userland threads" and you'll see that Mysql already has a bunch running. You can control how many in the mysql config, to optimize.

I expect if you issued several long running queries you'd see the threads get active and could see how much %CPU each was using.

---

### Post by elico on 2011-04-16
well there is a nice thing:
[http://www.anandtech.com/show/1713/5](http://www.anandtech.com/show/1713/5)

in any case there is support for more then one core using mysql but on versions 5.5 and 5.6 mysql are adding more features for this function.

and on mysql site:
[http://dev.mysql.com/doc/refman/5.0/en/mysql-threads.html](http://dev.mysql.com/doc/refman/5.0/en/mysql-threads.html)
[http://dev.mysql.com/doc/refman/5.1/en/mysql-threads.html](http://dev.mysql.com/doc/refman/5.1/en/mysql-threads.html)
[http://dev.mysql.com/doc/refman/5.5/en/mysql-threads.html](http://dev.mysql.com/doc/refman/5.5/en/mysql-threads.html)
[http://dev.mysql.com/doc/refman/5.6/en/mysql-threads.html](http://dev.mysql.com/doc/refman/5.6/en/mysql-threads.html)

---

