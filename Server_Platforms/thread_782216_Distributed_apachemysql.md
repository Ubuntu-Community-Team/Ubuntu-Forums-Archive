---
title: "Distributed apache/mysql"
date: 2008-05-04
forum: Server Platforms
---

### Post by maino82 on 2008-05-04
So here's the setup I'd like to achieve... I have 3 computers, one of which I'd like to act as a sort of passthrough machine that requests for port 80 will go to and then it will filter to either one of the other two machines, which will be clones of one another. 

My questions is, how can I accomplish this? I haven't really seen any tutorials that explain how to set this up, but I'm sure there have to be some out there... I'm probably just not searching for the right thing.

The main things I'm looking for instructions on are:

a) how to sync the 2 clone computers' web files (rsync I'm guessing, but don't know if there's a better way)
b) how do I keep the mysql databases in sync (again, rsync? Or is there a way to simultaneously write to both DBs when someone adds a record or something?)
c) how do I set up the passthrough to divide up the incoming port 80 requests and balance the load?
d) how do I set up the passthrough to silently transfer all load to one of the two computers if one of them fails?

I think a large portion of my problem comes from the fact that I'm unsure of terminology for a lot of this stuff. Any help anyone could offer would be greatly appreciated.

---

### Post by windependence on 2008-05-05
> **maino82 said:**
> So here's the setup I'd like to achieve... I have 3 computers, one of which I'd like to act as a sort of passthrough machine that requests for port 80 will go to and then it will filter to either one of the other two machines, which will be clones of one another. 

My questions is, how can I accomplish this? I haven't really seen any tutorials that explain how to set this up, but I'm sure there have to be some out there... I'm probably just not searching for the right thing.

The main things I'm looking for instructions on are:

a) how to sync the 2 clone computers' web files (rsync I'm guessing, but don't know if there's a better way)
b) how do I keep the mysql databases in sync (again, rsync? Or is there a way to simultaneously write to both DBs when someone adds a record or something?)
c) how do I set up the passthrough to divide up the incoming port 80 requests and balance the load?


d) how do I set up the passthrough to silently transfer all load to one of the two computers if one of them fails?

I think a large portion of my problem comes from the fact that I'm unsure of terminology for a lot of this stuff. Any help anyone could offer would be greatly appreciated.

What you are looking for is HA (high availability). There are quite a few ways to do this. Your MySQL databases have the built in ability to replicate to another node. If your web pages stay the same pretty much you could set up rsynch in cron every hour or so to synch your apache files and then just have the SQL data replicate across the two nodes. 

A more comprehensive solution would be the Linux High Availability project.

[http://www.linux-ha.org/](http://www.linux-ha.org/)

You also talked about load balancing. Again, there are several ways to accomplish this. Take a look at this link for more ideas:

[http://lcic.org/load_balancing.html](http://lcic.org/load_balancing.html)

Here is a good link for what I think you want to do:

[http://www.linuxvirtualserver.org/](http://www.linuxvirtualserver.org/)

And one more:

[http://www.cyberciti.biz/tips/load-balancer-open-source-software.html](http://www.cyberciti.biz/tips/load-balancer-open-source-software.html)

I'm working on one of these myself but I am using Virtualization and FreeBSD to cut down on the number of actual servers I need. Let me know if you have any success or tips if you get it working.

-Tim

---

### Post by maino82 on 2008-05-05
Tim,

Thanks for all the suggestions! I will look into these and keep notes on what I find while setting my stuff up. Hopefully I'll pick up a few good tidbits of info along the way.

Thanks again!
Dave

---

### Post by Chayak on 2008-05-06
If you're looking at load balancing you might want to check out Vyatta.  The new version 4 has a lot of nice functionality built in from routing, vpn, firewall, clusters, and load balancing.

If you want your mysql servers to sync you can set up replication between them.  The setup I have at one site has four slaves and one master.  Data is written to the master server and then replicates to the slaves which are the backend for the webservers.  They're all balanced using Vyatta routers.  There's no single point of failure in the setup and even if the master mysql server goes down one of the slaves is configured to take over the functions.

---

### Post by windependence on 2008-05-06
> **maino82 said:**
> Tim,

Thanks for all the suggestions! I will look into these and keep notes on what I find while setting my stuff up. Hopefully I'll pick up a few good tidbits of info along the way.

Thanks again!
Dave


Glad to help out. Shoot me an email or PM if you need any more help.

-Tim

---

### Post by maino82 on 2008-05-06
> **Chayak said:**
> If you're looking at load balancing you might want to check out Vyatta.  The new version 4 has a lot of nice functionality built in from routing, vpn, firewall, clusters, and load balancing.

If you want your mysql servers to sync you can set up replication between them.  The setup I have at one site has four slaves and one master.  Data is written to the master server and then replicates to the slaves which are the backend for the webservers.  They're all balanced using Vyatta routers.  There's no single point of failure in the setup and even if the master mysql server goes down one of the slaves is configured to take over the functions.

Chayak,

I'll have to look into Vyatta as well then. I've been looking at Linux-HA/heartbeat and I think that will serve my purpose nicely, but if Vyatta looks more like what I need I may give that a try. Thanks for the recommendation!

-Dave

---

