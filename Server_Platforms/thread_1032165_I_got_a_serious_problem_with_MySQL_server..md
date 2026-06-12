---
title: "I got a serious problem with MySQL server."
date: 2009-01-06
forum: Server Platforms
---

### Post by Mamsaac on 2009-01-06
When trying to run it:

> mamsaac@mamsaac-laptop:~$ sudo /etc/init.d/mysql start
df: `/media/MySQLDB/.': No such file or directory
df: no file systems processed
 * /etc/init.d/mysql: ERROR: The partition with /media/MySQLDB is too full!


My MySQL databases are in the partition /media/MySQLDB. It had been working fine (and I've been giving heavy use of it) until last restart. I'm not sure if I updated anything, but my first thought is that I might have done it (my brother was using my laptop and I was busy, so I told him to just update everything) and it broke some configuration file. The partition still has a little over 7gb available.

I searched a little on Google, but I feel really lost in this. Any ideas?

Thanks in advance.

---

### Post by Mamsaac on 2009-01-06
Fix'd the problem.

---

### Post by Iowan on 2009-01-06
What did you do (what fixed it)?
(And mark thread [SOLVED] (under Thread Tools)).

---

