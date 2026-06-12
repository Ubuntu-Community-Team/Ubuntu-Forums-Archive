---
title: "getting started mysql-cluster"
date: 2012-07-30
forum: Server Platforms
---

### Post by skrite on 2012-07-30
hey all. 
i need to know a few things before i move a large database from MyISAM to a new server setup with mysql-cluster. 

First, it is possible to leave some of my larger history tables in the MyISAM engine and access it with the same SQL server? If so, are there any dangers or gotchas to this besides the fact that it isn't replicated with the ndb tables? 

Second. How do i evaluate how many data nodes to run on each server? I plan to set this up with two servers (more probably later, depending on growth) and use two separate computers as the management nodes. If i have a replication on each of two machines, does it matter how i split the data up? How many nodes per machine should i run? 

The database is about 16.5 GB right now, and according to ndb_size.pl, i need 27.6 gb storage in data, and 8.5 in index. So more than 36 GB RAM minimal. Does this sound about right? 

Thanks for any tips here.

---

