---
title: "MySQL + rsync"
date: 2009-11-29
forum: Server Platforms
---

### Post by Vegan on 2009-11-29
If I was to have say several databases that were too big for a single server, can rsync maintain a decent working copy so that if the main database server dies data is not lost?

RAID6 can tolerate 2 disks fail, but other problems can bring a server down.

At present I am able to keep everything on a single server, but its growing bigger as time goes by.

---

### Post by Lars Noodén on 2009-11-29
[mysqldump](http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html) is probably the tool you are looking for.  Or else the perl script [mysqlhotcopy](http://dev.mysql.com/doc/refman/5.1/en/mysqlhotcopy.html). You can run it over ssh and pipe the data through gzip.  

[replication](http://dev.mysql.com/doc/refman/5.1/en/replication.html) might be another option for keeping a spare copy.  Keep a replica going, then lock all the tables for writing periodically to take back up snapshots.  

rsync can get the data if the database is shutdown, it is usually in /var/lib/mysql/, but if you try to use rsync or any other regular filesystem tool on a live database, you risk copying parts out of sync.

---

