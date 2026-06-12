---
title: "To Cloud or Not to Cloud"
date: 2010-10-28
forum: Ubuntu Cloud and Juju
---

### Post by brodsky on 2010-10-28
Hi All,
We provide a web based service.  Currently, we have one web server, and one backend MySQL server on two physical servers.
What we need is to be able to provision additional web or sql servers as demand grows, or shut them down again as demand decreases.  We would also like to be able to deploy test machines as required or "demo" machines as required.  This is why I am looking at the Ubuntu cloud approach.

This leaves us in the situation that we have no failover or scalability.
Is the Ubuntu Cloud a good solution for this situation?  If so, can anyone give me some pointers as to the correct hardware configuration to achieve scalability as well as failover/loadbalancing?
From my initial look through the Ubuntu Cloud site, I would suspect that we would need.
3 physical machines and one shared data store - NAS/SAN?
one server would be the Cloud Controller, booting off local disks
The other two machines, booting off local disks but using the external storage for vm's as a cluster.

Thanks in advance,
Leslie

---

### Post by kim0 on 2010-10-28
Hi Brodsky,

It seems you are asking about creating and using an "elastic" highly-available infrastructure. What follows is my own opinion

- For building a UEC based cloud, you'd need at least 2 servers (or more). The following notes might be useful
[http://open.eucalyptus.com/learn/InstallingECC](http://open.eucalyptus.com/learn/InstallingECC)


- A "cloud" like UEC, offers a scalable elastic infrastructure, however to utilize it, your application needs some intelligence, and your sysadmin processes too. SysAdmin processes need to evolve in order to be able to get a fresh machine, install it, register it, install apps, copy data take it to production all via automated scripts (or config management tools like puppet or chef or others). All that should be done in a few minutes. Let's go through an example. Assume you currently have 1 webserver and 1 DB server. Load increases a lot (slashdotted?) you need to spin up 10 additional web servers + 2 additional read-only DB replicas. Here's what you need

  - You need 10+2 = 12 new virtual servers. UEC gives you that easily
  - You need to "deploy" those 12 fresh machines into their "roles" of "web" servers and DB replica servers. UEC is not involved here. Your sysadmin processes and config management tools need to be ready to do this
  - Your load balancer (if you don't have one you need to get one) should be configured to spread some the load to the new boxes. Again config management
  - Your "application" needs to know how to work and utilize those 10 new web servers. i.e. it needs to scale, handle transactions, handle sessions ...etc This is an application problem. If your app cannot do that today, it might need to be re-written or modified at least

Also in cloud contexts, people don't normally target clustering/failover. If a virtual/physical server fails, your monitoring system should detect that, UEC should be asked to provide alternate servers, your tools should engage to deploy the new servers into production. Servers are in essence stateless. If a server wants to die, it can die, I can replace it anyday. That's the cloud spirit :) While the clustering spirit was, if a server wants to die, I won't let it

I hope this was useful
All the best

---

### Post by brodsky on 2010-10-29
Thanks for the detailed answer Kim0 :)

---

