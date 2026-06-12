---
title: "I need some guidance on large storage needs."
date: 2019-12-01
forum: Server Platforms
---

### Post by pepsifx357 on 2019-12-01
I own an ISP and I'm also friends with another local ISP.  We both want to setup cloud storage, a streaming media server, and eventually hosting services for our customers, so we're wanting an easily scalable storage system and a clustered VM environment.  Basically we're starting a small data center.  I want a system where we can easily scale out either storage or horsepower or both.  My current idea is as follows:

> We want to initially start with 6 servers.

> 3 of them will be Freenas systems with a 20TB pool each using RaidZ2 on 6 hard drives.

> These Freenas systems will also host an Ubuntu server running glusterfs for a total of 3 nodes, to begin with.

> The other 3 (physical) servers will provide VM horsepower via oVirt in a clustered environment with the Ubuntu/gluster nodes providing the storage backend.

> All 6 servers will be connected to a dedicated 10Gb aggregate switch.

The reason I want to do it this way is so that we can lose 2 hard drives per server or an entire Freenas/Ubuntu server and still be ok and running.  oVirt allows you to easily connect to a glusterfs backend for storage and easily sets up a VM cluster environment, which is the reason I chose that over other offerings like Proxmox, Xen, ect.  According to oVirt if we were to lose one of the 3 servers, the VMs on that server would failover to the other 2.  I like that idea.

This is my rough draft.  I'm pretty new to clustered environments.  I've looked into maas, openstack, and ceph but I could never get all that working in order to create a proof of concept or determine whether or not maas/openstack or ceph was what I needed.  If someone were to nudge me in any of those directions, I would take the time to learn, make them work and test them out.  I was kinda hoping someone would chime in and either stop me from making a terrible decision and steer me in the right direction or tell me I'm on the right track.  I don't want to set all of this up, only to realize there is some critical limit in the future when we go to add more Freenas/Ubuntu servers for more storage or that this system will be horribly slow when we add more storage.  I'm open to any and all possibilities...open source of course. :)

I've included a chart that might help show what I'm wanting to do.

---

### Post by gnusci on 2019-12-01
Looks good to me, just let us know once is running. Just test performance and efficiency, but also take care if you will require scalability. search in for "benchmark datacenter storage".

---

