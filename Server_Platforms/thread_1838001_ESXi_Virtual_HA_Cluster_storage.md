---
title: "ESXi Virtual HA Cluster storage"
date: 2011-09-02
forum: Server Platforms
---

### Post by kyleh0000 on 2011-09-02
Hi All :)

I'm a sys admin at a school and we are about to purachse a blade/san setup to run all of our services virtualised within ESXi. We are still in the early planning stages so I'm just trying to get my head around how it all needs to come together.

I would like to setup a Linux HA file cluster virtualised within the ESXi, however the issue I'm running into is shared storage for user data.

We have a test instance of ESXi just running on a single server for me to do all my testing which is so far going very well, I have managed to setup my HA cluster within ESXi using NFS for the shared storage which all works fine. 

The above setup was assuming we have a SAN setup that uses NFS to share storage. However I would like to get this setup working without the need for NFS shared storage.

The reason for this is we already have a bunch of RAIDs which are capable of being turned into a FC SAN we just need to get the FC Switches to connect them up, this is going to be a much cheaper option compared to getting a whole new SAN setup. So I would like to connect the FC Switches and our current RAID hardware to our blade chassis and create an ESXi HA Cluster, with a HA Ubuntu cluster running inside using ESXi to serve the share storage.

My thinking was that I can create a Virtual Disk connect that to the cluster nodes within ESXi then use GlusterFS (or similar) to managed the shared storage, I had a look at this guide which seems to cover most of the steps for implementing GlusterFS.

[http://www.howtoforge.com/high-availability-storage-cluster-with-glusterfs-on-ubuntu-p2]("http://www.howtoforge.com/high-availability-storage-cluster-with-glusterfs-on-ubuntu-p2")


Has anyone had an experiences with a similar setup or if not can anyone point me in the right direction to get more information?

Thanks again for your advice

---

