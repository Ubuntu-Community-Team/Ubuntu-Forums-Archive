---
title: "partitioning + video streaming + clustering + load balancing"
date: 2009-03-31
forum: Server Platforms
---

### Post by bluethundr on 2009-03-31
Hi guys, 

I've been an Ubuntu hobbyist for a long time! Guess what? I just got my first ever JOB doing what I love... Ubuntu! 

Here's the thing. My partitioning schemes have always been... simple. I've never had a need as far as I could tell to come up with complex partitioning schemes. 

Let me go over briefly what I've been asked to do (without violating my NDA, so some details will be sparse). 

I have been asked to setup a video streaming website that will also transact financial transactions for each video viewed. 

We will be using Apache + Tomcat and keep track of the transactions using a MySQL database. 

We will have one Apache server, and two database servers. The database servers will need to be clustered. 

Here are the issues that I need to get up to speed on in a hurry in order to turn Ubuntu into something more than a pleasant pass time and something that I can actually earn a living at. 

I need to come up with a sensible partitioning scheme to do the above. 

I need to figure out how to stream video. 

I need to figure out how to do clustering for the database server and that server will need to be load balanced. 

I would need help with partitioning, streaming video and clustering. Also it should be noted that my experience with load balancing is limited and I could use some pointers there too. 

If you would like any more information, I will do my best to accommodate your request. :popcorn:

---

### Post by HermanAB on 2009-03-31
Some pointers:
Not sure why you want to cluster the DB, since most of the load will be on the web server.
Do install VMware and do *everything* in virtual machines.  That makes it much easier to move things around to new or more powerful hardware.  Your boss will love you and give you a raise the first time you need to move things around.
VMware has a cluster solution too to use one day when you really need it.
Partitions guard against runaway problems that can fill up a disk and render the system unbootable.  For a server, /boot, /, /swap, /home /var is good and maybe /usr.
Do use XFS.
Do use a UPS.
Do use two independent internet connections.

---

### Post by bluethundr on 2009-03-31
Thanks! My boss is telling me that we expect heavy transactions on the MySQL database due to the largely financial nature of the site. That's why he's recommending clustering and load balancing.


And sorry, but I am not clear in what way you are suggesting I use VMware. Could you elaborate on that point?

Thanks!


> **HermanAB said:**
> Some pointers:
Not sure why you want to cluster the DB, since most of the load will be on the web server.
Do install VMware and do *everything* in virtual machines.  That makes it much easier to move things around to new or more powerful hardware.  Your boss will love you and give you a raise the first time you need to move things around.
VMware has a cluster solution too to use one day when you really need it.
Partitions guard against runaway problems that can fill up a disk and render the system unbootable.  For a server, /boot, /, /swap, /home /var is good and maybe /usr.
Do use XFS.
Do use a UPS.
Do use two independent internet connections.

---

### Post by HermanAB on 2009-03-31
You have to pick hardware that is supported by VMware ESXi.  You can then layer various VMware tools on top of that one day when you need it.  VMware has a vCloud (or some such) solution that will do the clustering for you, but these tools all rely on ESXi at the bottom and it only runs on a limited set of server hardware.

You can start with simple virtual machines on ESXi for each function on one or two physical servers.  Then as the load dictates, you can move the VMs to different machines or to cluster machines, without missing a beat.

Go to the VMware web site and start reading.  It will be time well spent.

---

### Post by bluethundr on 2009-03-31
Thanks Herman. 

Actually the "servers" just arrived. Seems like folly, but I recommended they get _actual_ server hardware (from eBay if need be to cut costs) but instead they stuck me with 4 Dell Optiplex 755 Desktops. :|

And somehow they expect me to work my "magic" and make a video streaming site happen for them??? Oh well, I guess I'll do what I can.

Boxen came with Red Hat on them... I am reinstalling Ubuntu Server on them.. need to have an OS I am familiar with...

> **HermanAB said:**
> You have to pick hardware that is supported by VMware ESXi.  You can then layer various VMware tools on top of that one day when you need it.  VMware has a vCloud (or some such) solution that will do the clustering for you, but these tools all rely on ESXi at the bottom and it only runs on a limited set of server hardware.

You can start with simple virtual machines on ESXi for each function on one or two physical servers.  Then as the load dictates, you can move the VMs to different machines or to cluster machines, without missing a beat.

Go to the VMware web site and start reading.  It will be time well spent.

---

### Post by bluethundr on 2009-03-31
NO budget for VMware... how about Xen? I heard that was good...

---

### Post by bluethundr on 2009-03-31
Also I'm using a 350GB drive. What sizes do you suggest for these partitions?

> 
For a server, /boot, /, /swap, /home /var is good and maybe /usr.


---

### Post by bluethundr on 2009-03-31
Correction... I have a 250 GB drive...

---

### Post by bluethundr on 2009-03-31
Correction... I have a 250 GB drive...

---

