---
title: "VMs in the Cloud"
date: 2012-02-09
forum: Ubuntu Cloud and Juju
---

### Post by jerim79 on 2012-02-09
I am working on a project where we have six Dell Optiplex 960 desktop machines. We are wanting to create a high availability cluster out of the six desktops. By high availability I mean we want to basically have all the processing and data storage spread out over the six systems evenly as though they were one server. Think of a RAID 5. 

If one system goes down, we simply replace it with another system and the cluster will rebuild the data that was on the broken system. Until we replace the node, the cluster just operates on reduced capacity. I have read of setups similar to this but there is always a management PC involved. Which means if the management PC goes down, then the whole system dies. The idea is to have a completely automated cluster that doesn't need human intervention at 2am if one of the nodes goes out. 

Once we get that in place, we are going to use the cluster for serving up VMs to our thin clients (Other virtual desktop solutions just don't meet our needs). I am only mentioning this as I want to give everyone a clear picture of what we are trying to accomplish. If a node in the cluster goes out, we want the other nodes in the cluster to continue serving up all the VMs. We are a branch location of a much larger organization. They have the local network locked down tight with proxy and domain servers. I am not really able to test out UEC as I can't access the internet. 

Anyone have any thoughts on implementing a high availability cluster with redundant nodes and automatic failover? Can UEC get the job done or am I looking for some other technology?

---

### Post by jerim79 on 2012-02-14
What I was looking for was this:
[http://www.drbd.org/](http://www.drbd.org/)

Does clustering with HA and even has support for VMs.

---

