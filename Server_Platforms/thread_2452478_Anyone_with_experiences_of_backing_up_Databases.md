---
title: "Anyone with experiences of backing up Databases?"
date: 2020-10-22
forum: Server Platforms
---

### Post by kevdog on 2020-10-22
I have home docker bitwarden_rs project. It's really neat to play with.  Like many web applications it stores its data within a backend database.  I'm not sophisticated enough at this moment to run a K8 cluster, but I am capable of running a docker swarm where I can have two nodes for the actual application layer running within two separate VM's located on different machines but all within the same LAN space.  In terms of High Availability and Failover protection, the only part of my design I haven't been able to "replicate" successfully is probably the most important part of the project -- the database backend.  Currently I have a postgresql docker instance with bind mounted storage running on the master node.  If the database somehow becomes corrupted, destroyed, etc -- the data is a total loss.

Although there are options for the project to have a mariadb or sqlite backend, I've been doing some reading on database replication and it seems specifically postgresql was designed with this feature set in mind.  I ran across this article discussing simplified examples of configuring replicated postgresql databases with asynchronous/synchronous backup [https://luppeng.wordpress.com/2019/06/02/postgresql-11-warm-standby-failover-log-shipping-for-high-availability-in-docker/](https://luppeng.wordpress.com/2019/06/02/postgresql-11-warm-standby-failover-log-shipping-for-high-availability-in-docker/).  Before I started down yet another rabbit hole I was wondering if any of the IT pros had any experience in general in the area of database replication/fail-over.  I'm aware there are many commercial products that provide software to accomplish this, however I was looking for something more appropriate for a home lab.  Others I've talked to admit the difficulty with working with databases and have defaulted to using something like an Amazon database so they don't have to worry about managing backups etc.  Others have suggested I'm making it too hard and I should take a simplified approach of dumping the data on set intervals (like nightly for my small project) and keep "x" numbers of backups in case a restore is necessary.  Just wondering what kind of approach has been tried and works well.

---

### Post by SeijiSensei on 2020-10-23
I've used PostgresQL for two decades now and would never choose another DBMS.  

For backups, I run "pg_dump" every night to create a plain-text backup of the database.  I suck these over to my home office server where they are backed up.   I run a script that connects to each database and dumps the contents to a unique file.  
```

# get list of databases
DBLIST=$(echo 'select datname from pg_database;' | psql -U postgres template1 | grep '^\ ' | tail -n+3)

for db in $DBLIST
do
    pg_dump -U postgres $db > $db.psql
    gzip $db.psql
done

```

I've never used PG's replication systems though I understand they are quite robust.  I'm just running PHP applications on a few servers which access a database via localhost. I haven't had any issues with the DBMS failing in these simple setups.

---

### Post by LHammonds on 2020-10-24
> **SeijiSensei said:**
> ...
The subject line is misleading.  The subject is actually about replication....not backup.   I have done standalone, clustered databases and backups but not replication between 2 databases.

If I needed HA, I went with a [DB cluster](https://hammondslegacy.com/forum/viewtopic.php?p=713#p713) and [proxy front-end](https://hammondslegacy.com/forum/viewtopic.php?p=722#p722).

LHammonds

---

### Post by kevdog on 2020-10-26
@LHammonds and @SeijiSensei -- the examples you have posted are really helpful and they give me a lot to think about.  I guess my first priority as this is a home project is making regular backups of the database to prevent data loss. After I have a reasonable and tolerable solution, I'd probably move into configuring a warm or hot spare if need be.  I've used mostly mariadb like databases in the past, however just learning about postgresql.  I'm still exploring options between the two.  I'm doing most of my tests within docker containers with a swarm setup, although I suppose this isn't exactly necessary.  @LHammonds -- some of the example of communication between different VMs is really helpful.  

Thanks for all the efforts you guys put into the posts.

---

