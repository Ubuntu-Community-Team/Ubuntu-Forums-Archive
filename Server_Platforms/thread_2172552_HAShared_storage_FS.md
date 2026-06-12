---
title: "HA/Shared storage FS"
date: 2013-09-05
forum: Server Platforms
---

### Post by nhybgtvfr on 2013-09-05
Hi,

I have a couple of Ubuntu 12.04 servers running as storage servers. they are running drbd and heartbeat to provide high-availability iscsi storage used as an SR to a 4 node xenserver pool (6.2) everything on that is working brilliantly.:D
the iscsi storage holds the xenserver pools virtual machine disk images. 
there are going to be multiple webserver vm's as a server farm in the xenserver pool, I want all the website data to be on shared storage as well, separate from the disk images, so that each webserver can serve up every website, 
I've added more disks, and installed nfs-kernel-server to the 2 Ubuntu storage servers, again using drbd and heartbeat to provide replication/failover. this is working fine, as far as high-availability/failover goes, but not for writing to the share, the drbd device is currently using the jfs file system. the webservers must be able to write to each websites stats/log files concurrently. 
can I just change that to gfs2/ocfs2 and concurrent writing will be fine? or do I need to move away from nfs completely? 

what is the recommended fs/configuration for this scenario? I've been reading what I can find about gfs/ocfs/glusterFS/nfs etc, but the more I read the more confusing and contradictory it all seems to be.


thanks
lee.

---

