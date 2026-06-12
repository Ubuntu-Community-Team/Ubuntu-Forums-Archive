---
title: "Block Level Replication?"
date: 2008-08-17
forum: Server Platforms
---

### Post by e30drift on 2008-08-17
I am trying to setup a off-site data store backup with block level replication.  

Currently I have T1 connections between 2 site joined by a site-to-site VPN between 2 Sonicwall firewalls.  This T1 will be dedicated for replication and file access between the sites.  Internet traffic is going through another connection.  

I plan on deploying 2 Ubuntu Server 8.04 and a iSCSI SAN at both sites.  

The problem is that both sites require data from either site.  I want to be able to replicate the data between the sites at the block level.
Currently I have an Exchange 2007 DB on the SAN and it is super important that I can replicate that at the block level.

Current solutions involve companies like NetApp.  They have amazing products, but the cost is out of the question by my management.  

I was wondering if anyone had any experience with this kind of setup or perhaps a better idea.

---

### Post by windependence on 2008-08-17
Have a look at this:

[http://www.drbd.org/](http://www.drbd.org/)

You would have to have a good connection between the nodes but I think with the dedicated lines you would be OK.

-Tim

---

