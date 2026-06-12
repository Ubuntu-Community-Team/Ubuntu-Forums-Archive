---
title: "NFS server causing clients to generate high load"
date: 2013-01-19
forum: Server Platforms
---

### Post by noahwatkins on 2013-01-19
We have a 12.04.1 LTS Ubuntu Server, and about 40 client nodes also running the same distribution. We recently upgraded (security / bug fixes) the server, and started to see very strange behavior.

After a reboot load on the server is normal. After a while all of the NFS threads start to overload the CPU. We can see form ifstat that the server is receiving 10's of MB/s of network traffic from our clients.

Looking at the clients we see an NFS client kernel thread [192.168.140.2-m] producing a lot of network traffic to the server, even though on each client there is no other application using NFS.

We were able to look at the conversation between the server the clients:

The clients are repeatedly sending SETCLIENTID_CONFIRM, and the server responds every time immediately with NFS4ERR_STALE_CLIENTID. (The nodes are also sending SETCLIENTID, but the server responds successfully to that.)

Any help would be appreciated. We are a university lab ran mostly by grad students. This cluster has been performing great for a long time with the same configuration.

---

