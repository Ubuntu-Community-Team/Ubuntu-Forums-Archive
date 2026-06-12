---
title: "Large MySQL-files"
date: 2008-07-28
forum: Server Platforms
---

### Post by yc2 on 2008-07-28
I have a small homepage. It uses MySQL for Drupal and a newly installed search-engine (sphider.eu). It is just a hobby, activity is very low and I make occasional backups with phpMyadmin.

However, I am a little interested in how the MySQL database files should be treated if activity on my homepage would increase. I assume MySQL-files would eventually become so large that they would be difficult to handle on the server and for backup? If you add the possibility to store pictures and  even films in the database, maybe this could become a real problem.

Eventually the MySQL files could exceed the size of the disk. Are they managable for usage by the server when this situation approaches? If they grow further, how do you treat the problem. Buy a bigger disk? Is RAID something one can use here?? I usually keep my page on my Ubuntu computer at home, but from time to time it has to reside on a web-hotel.

Maybe other precautions must be taken if activity increases on the page??

A theoretical question from the perspective of my small homepage, but is is usually good to know the directions in which matters can develop. ;)

Thanks :)

---

### Post by cariboo on 2008-07-28
Mysql databases are located in /var/lib/mysql, so either have a seperate and large /var partition, or make sure your root partition has enough to keep up with the size of your database.

Jim

---

### Post by tinny on 2008-07-28
Disks only have so much space. This is what ive done in the past...

As a database server started to max out the disk space I took it offline at say 1am and did a [mysqldump]("http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html"). Then I restored the dump onto a new MySQL server build (a machine with a much bigger HD, this could be the same machine rebuilt with a bigger HD).

Having a replicated MySQL setup helps keep you "up" while you are running the migration of the main MySQL server (replicated slave takes the load in read only mode while you are migrating). 

[http://dev.mysql.com/doc/refman/5.0/en/replication.html](http://dev.mysql.com/doc/refman/5.0/en/replication.html)

Basically you have to be very careful when running this type of operation...

---

### Post by cdtech on 2008-07-28
You can have your database anywhere you want and on whatever drive you prefer as long as you point your configuration files to that database. If you find that your database is growing beyond the size of your current location, its just a matter of dumping your database to a new location or drive.

**P.S.**
Sorry tinny, just like he said. I posted a little late. lol

---

### Post by tinny on 2008-07-28
> **cdtech said:**
> You can have your database anywhere you want and on whatever drive you prefer as long as you point your configuration files to that database. If you find that your database is growing beyond the size of your current location, its just a matter of dumping your database to a new location or drive.

**P.S.**
Sorry tinny, just like he said. I posted a little late. lol

It was good that you mentioned pointing the config to another drive. You dont have to rebuild the server

---

### Post by yc2 on 2008-07-29
Thank you all for clear and useful information. :KS

---

### Post by hyper_ch on 2008-07-29
it takes a lot for 1 mysql db to become 1gb in size... especially if no blobs are stored inside.

---

### Post by Cadmus on 2008-07-29
If you're getting to sillily large dbs is the preferred MySQL solution to start clustering?

---

### Post by tinny on 2008-07-29
> **Cadmus said:**
> If you're getting to sillily large dbs is the preferred MySQL solution to start clustering?

NO!!!

Right now MySQL only supports in memory clustering. Thats a lot of RAM / nodes if you are using clustering as a solution for a very large db.

Clustering is generally used as a solution for high availability, 5 9's availability. (99.999% up time)

FYI...

[http://en.wikipedia.org/wiki/MySQL_Cluster](http://en.wikipedia.org/wiki/MySQL_Cluster)

---

### Post by yc2 on 2008-07-30
Thanks all for considering my question even though my homepage is just small-time so far. Considering the problem helps understanding and preventing problems.

I found this in the MySQL manual, I can't really say how it applies.

> Maximum data file size: The theoretical limit is 64G; however, in MySQL 5.1, the practical upper limit is 32G. This is equivalent to 32768 extents of 1M each. [http://dev.mysql.com/doc/refman/5.1/en/mysql-cluster-limitations-disk-data.html](http://dev.mysql.com/doc/refman/5.1/en/mysql-cluster-limitations-disk-data.html)

I am not sure my question is well put, but if my datafile (maybe mostly one variable in it) would start approaching 32G, what can I do?

Maybe the conclusion is that one should not store large volume data in MySQL-database?

---

### Post by tinny on 2008-07-30
> **yc2 said:**
> Thanks all for considering my question even though my homepage is just small-time so far. Considering the problem helps understanding and preventing problems.

I found this in the MySQL manual, I can't really say how it applies.

[http://dev.mysql.com/doc/refman/5.1/en/mysql-cluster-limitations-disk-data.html](http://dev.mysql.com/doc/refman/5.1/en/mysql-cluster-limitations-disk-data.html)

I am not sure my question is well put, but if my datafile (maybe mostly one variable in it) would start approaching 32G, what can I do?

Maybe the conclusion is that one should not store large volume data in MySQL-database?

Database partitioning.

---

