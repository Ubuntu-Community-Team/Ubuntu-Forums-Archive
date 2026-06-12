---
title: "fault tolerance"
date: 2008-11-11
forum: Server Platforms
---

### Post by stevezemlicka on 2008-11-11
Currently we have an ubuntu server hosting vmware server.  it works great but I am looking to gain fault tolerance.  Currently the vmware disk images are stored locally on the server's raid array (raid 5).

We have two identical servers I was hoping to setup as a fault tolerant san.  I would like to install identical raid arrays into both these servers and have one server as the primary and the second one as the failover.  Is this possible with ubuntu?  Can I setup two machines to appear as one.

If that is possible, then I would like to setup a second ubuntu vmware server that can either pickup where the primary vmware server left off or, worst case, just boot up those vmware machines.

---

### Post by HermanAB on 2008-11-11
You need to look at the heartbeat project:
[http://www.linux-ha.org/](http://www.linux-ha.org/)

Cheers,

Herman

---

### Post by sr20ve on 2008-11-11
I don't want to say that's not possible, but it sounds like you're really trying to push the limits on what vmware server was designed for.

I would recommend going with esx, or the free esxi. Then you could pick up a cheap iscsi san to house your VMs and setup an HA cluster, but you would have to purchase a virtual center license with vmotion and HA. 

Not sure if that's the answer you're looking for..

---

### Post by stevezemlicka on 2008-11-11
My concern with a SAN is that without purchasing multiple devices, we will have a single point of failure.  Plus, san devices get pretty expensive when you need TBs of space like we do, especially when you have to purchase multiple devices for fault tolerance.

I am very interested in that heartbeat program.  It sounds like that may provide.  Just not quite sure it'll work for running two active vmware servers.  It might be perfect for the fault tolerant storage systems though.

---

### Post by PilotJLR on 2008-11-12
Really the point of a SAN is to NOT have a single point of failure... which is why they are so expensive.  :-)

Keep in mind there are two separate needs here... one need for redundant storage, and another for HA for services or VM's. Both are necessary, and there is no single solution to meet both needs.

The best way to do this is with a real SAN and VMware Infrastructure. This would of course, get pricey. You can mitigate some cost by using iSCSI and an entry level san, like Lefthand.

---

### Post by PilotJLR on 2008-11-12
One more point - talking about VMware's HA feature, that is not free. It requires a VI Standard or VI Enterprise host license and one VCMS.

A manual cold migration is, of course, free and can be done with ESXi on a free download.

---

