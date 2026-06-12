---
title: "Ubuntu Failover Cluster Questions"
date: 2010-04-26
forum: Server Platforms
---

### Post by madhatter563 on 2010-04-26
I've been reading up on clustering a bit and want to create simple 2 machine cluster of which the 2nd one will turn on and take over traffic at the previous machine's IP (I'm aware there will be a couple minutes of downtime while the failover server boots).  

I've looked into doing a simple DNS round robin, but I think both machines would need to be online all the time for this to function correctly.

I've also looked into linux-HA and GlusterFS but both seem a little intense for the simple failover I'm trying to achieve.  

One catch if approaching with DNS round robin... the server that I want to setup with a failover also operates as a DNS server.

Anyone know the simplest way to complete this?

One idea I had (that seemed like a bit of manual work):
Create script that runs every 60 secs through CRON on firewall (running pfsense) and have it check if master-server is up.  If it's not, it will send a WOL signal to the slave, which has a mirrored image of the first.

the problem I have with that is I will also need to create a script to keep both synced properly which seems almost impossible if one is shut down until failover (my thought was periodic rsyncs.)  Perhaps creating a FS to direct all files to for the master/slave would be the only way around that.

Any ideas appreciated!

---

### Post by NullHead on 2010-04-26
What if you just stored the important info on a NAS in raid 1 and mounted the location with NFS or similar? 

As far as the clustering thing and the fault tolerance goes, that's completely out of my league.

---

