---
title: "MySQL Master &gt; Slave Replication (One slave for three masters?)"
date: 2011-09-06
forum: Server Platforms
---

### Post by JoeSabido on 2011-09-06
Scenario:

- There are 3 MySQL database servers on different locations (DBServer1, DBServer2, DBServer3)
- Each DBServer has a single database called EMPLOYEES

Is it possible to have another server (let's call it DBMirror) that acts as a slave shared among the DBServers?

What I'd like to do, is to create 3 databases on DBMirror (EMPLOYEES_1, EMPLOYEES_2, EMPLOYEES_3) and each of those databases would be a slave to the EMPLOYEES database on its correspondent DBServer.

In other words, in DBMirror there would be:
- A database EMPLOYEES_1 which is a slave of the EMPLOYEES database on DBServer1
- A database EMPLOYEES_2 which is a slave of the EMPLOYEES database on DBServer2
- A database EMPLOYEES_3 which is a slave of the EMPLOYEES database on DBServer3

Is this possible? How do I achieve this? Most I've read deals with 1 Master / 1 Slave combinations or Multimaster / Circular replication, but it doesn't LOOK like what I want.

Thanks!

---

### Post by zackwasa on 2011-09-08
Hi,

One solution would be to run 3 separate mysql servers on the slave server each on a different port and different data directory location.

---

### Post by JoeSabido on 2011-09-08
> **zackwasa said:**
> Hi,

One solution would be to run 3 separate mysql servers on the slave server each on a different port and different data directory location.

Thank you for replying. 

I thought of this, but I used the number 3 as an example, the actual number of servers is 28, and I have the impression that managing 28 MySQL instances can get very cumbersome and maybe use lots and lots of RAM?

---

### Post by spynappels on 2011-09-09
Will the slave be read from in each instance, or is it simply to provide a backup of the data?

---

### Post by zackwasa on 2011-09-09
You can't achieve what you want the way you want it. The only way is to have each master server use a different name for the db:
master1 - dbname1
master2 - dbname2
...

---

