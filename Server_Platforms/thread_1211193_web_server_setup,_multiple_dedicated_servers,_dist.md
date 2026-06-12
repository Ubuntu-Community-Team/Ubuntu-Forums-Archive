---
title: "web server setup, multiple dedicated servers, distrubited with round robin?"
date: 2009-07-12
forum: Server Platforms
---

### Post by greggatghc on 2009-07-12
I am looking to rebuild some hosting setups I have.  Currently I have access to 6 dedicated boxes, each one in a different data center in the world (on 3 continents.)  I would like to change these from individual installs of debian or ubuntu server with their own configs, software and so on.  

So what software out there should I be looking at to turn this into a solid hosting solution.  I would like all of the files available from all of the servers and if possible geo-location to be part of the dns solution so it sends the data from the closest server.  I would also like the databases to be distributed for cpu and file i/o load balancing of some kind.  Redundancy of the data and the possibility of partitioning needs to be taken into account I would think.

These are my random thoughts, any suggestions on projects to check out?  The code powering current sites on the servers is going to be re-written from scratch ontop of the new hosting solution once its ready so backwards compatibility is not a problem.

---

### Post by greggatghc on 2009-07-12
Somewhat answering my own question via howtoforge.com  I am thinking about mixing these 3 tutorials together to provide the solution.

[http://howtoforge.com/setting-up-a-high-availability-load-balancer-with-haproxy-heartbeat-on-debian-lenny](http://howtoforge.com/setting-up-a-high-availability-load-balancer-with-haproxy-heartbeat-on-debian-lenny)

[http://howtoforge.com/distributed-replicated-storage-across-four-storage-nodes-with-glusterfs-on-debian-lenny](http://howtoforge.com/distributed-replicated-storage-across-four-storage-nodes-with-glusterfs-on-debian-lenny)

and

[http://howtoforge.com/setting-up-master-master-replication-on-four-nodes-with-mysql-5-on-debian-etch](http://howtoforge.com/setting-up-master-master-replication-on-four-nodes-with-mysql-5-on-debian-etch)

---

