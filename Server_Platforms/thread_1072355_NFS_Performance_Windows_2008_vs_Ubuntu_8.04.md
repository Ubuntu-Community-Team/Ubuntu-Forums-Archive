---
title: "NFS Performance Windows 2008 vs Ubuntu 8.04"
date: 2009-02-17
forum: Server Platforms
---

### Post by AndyMcCall on 2009-02-17
Hi Folks,

I am working on a large virtual learning environment platform for around 40000+ students.  Part of this system requires 40Tb SAN space to be shared out via NFS and mounted on 6 Ubuntu 8.04 LTS servers.  These servers are redundant to each other, although the 40Tb would only be mounted and shared out from one server.

The options I have for the NFS share is to share it from one of the 6 Ubuntu 8.04 LTS servers or shared out from an existing Windows 2008 cluster.

Initially I thought NFS and Linux go hand-in-hand, but after thinking about it a bit more I started wondering if it might be better to go with the NFS share coming from the Windows 2008 cluster for redundancy reasons (i.e. loosing a single NFS serer won't kill the share).

Does anyone know anything about NFS performance on Windows 2008 vs NFS performance on Linux?  If the performance is the same then the cluster is probably better, but if Linux is by far faster then it might be worth the single-server risk.

Maybe I am thinking of it all wrong and there is a better way to mount the 40Tb than on just one server...

I know posts of this nature can become a little bit heated... This isn't a request for a flame war, I don't really care which OS is "better" or more "l33t" :) - I am an admin in a real world situation looking for advice from other Linux admins who may have been in the similar situation.

Thanks in advance!

---

### Post by HermanAB on 2009-02-17
Hmm, I haven't tested Win2008, but on 2003, NFS was roughly half the speed compared to a similar Linux system.  Gawd knows why.

It is easy to test though.  Install Services for Unix on Win2008, create a 10GB file on a Linux client and time the transfer:

Make a large test file that will overwhelm all buffering:
$ dd bs=1000000 count=10000 if=/dev/urandom of=10gb

Copy it:
$ date;cp 10gb /mnt/nfsshare;date

and get the old calculator
$ kcalc

Cheers,

Herman

---

### Post by Fire_Chief on 2009-02-17
You may want to look at a different structure for your NFS cluster. In normal NFS clusters, each node keeps a copy of the data, only one node is actively being used (others are in standby/passive mode), and all data changes are replicated to the other nodes to keep them in sync. While this is okay for a file server style setup that is moderate to low utilization, it is very inefficient for something of the size you are talking about. (I'm not saying it won't work but you have other options worth exploring.)

Have a look at GFS (or GFS2) for the backend. It was released by RedHat and is available for Ubuntu in the repositories. It would allow you to use all 6 Ubuntu servers actively and spread the user connections across all of them for better scalability, performance, and availability. You could still use NFS for the front end connections but then don't have to worry about the locking issues as GFS would manage the backend.

See [this]("http://books.google.com/books?id=LhMFril7EBgC&pg=PA232&lpg=PA232&dq=Linux+GFS+cluster+on+Ubuntu&source=web&ots=aM-ZnN6Jzl&sig=uuw-Pfp7fUb_eyBunFqvesC71XQ&hl=en&ei=DtmaSbitBJmEyAXNyqSYCg&sa=X&oi=book_result&resnum=8&ct=result") for some info.

Cheers!

---

### Post by AndyMcCall on 2009-02-17
I am not sure if I am on the same wavelength here, but...

The 40Tb is on a SAN and is presented to the OS as a single drive. Ifs the file system was shared out via the Windows cluster then the same 40Tb would be presented and mounted via Windows and if one node went down, the other would carry on with the networking.  No data would be duplicated in a standby/passive mode.

I *think* your saying that if the data was shared via a Linux-based cluser I would actually need two 40Tb drives?  If this is the case, then I simply can't do that as I only have one lot of 40Tb space.

If there was a file system that multiple servers could mount directly then that would work as I could mount the SAN presentation on server A) and server B) and set NFS HA between the two, which is essentially what Windows does (or so I have been told by our Windows admins!)

---

### Post by HermanAB on 2009-02-17
BTW, depending on your network, you should also try jumbo frames to improve throughput on gigabit networks:
ifconfig eth0 mtu 9000

This can make a huge difference.

Cheers,

Herman

---

### Post by Fire_Chief on 2009-02-17
> **AndyMcCall said:**
> The 40Tb is on a SAN and is presented to the OS as a single drive. If the file system was shared out via the Windows cluster then the same 40Tb would be presented and mounted via Windows and if one node went down, the other would carry on with the networking.  No data would be duplicated in a standby/passive mode.
That is correct. Typical Windows clustering with a SAN is the failover type where you have an active node and passive node(s). When one fails, the other one then becomes active and picks up for the downed server. 

> I *think* your saying that if the data was shared via a Linux-based cluster I would actually need two 40Tb drives?  If this is the case, then I simply can't do that as I only have one lot of 40Tb space. This would be the case if you were to setup a *typical* NFS cluster with DRBD and Heartbeat. 

> If there was a file system that multiple servers could mount directly then that would work as I could mount the SAN presentation on server A) and server B) and set NFS HA between the two, which is essentially what Windows does (or so I have been told by our Windows admins!) This is how GFS would work on the backend in Linux. It would allow multiple servers to "see" and touch the same data simultaneously (or close enough that you can't tell). I don't think you would need to configure NFS HA though. You should be able to configure all 6 servers to be "active" nodes though each one would not need to know about the others on the frontend of things. The GFS system would manage the connections from the servers to the SAN data to prevent locking issues and manage data consistency.

Windows does not do this natively (simultaneous access to one data set from multiple machines). The application itself has to be "cluster-aware" for that to work (note this is the same for apps on Linux like NFS). Microsoft suggests when configuring a multi-node cluster, to section off access to the data so that each server manages a portion of the data. It can then failover to another server if needed by handing control of that data access to another active server.

This can be done on Windows by implementing a true, multi-node file system such as the PolyServe File System. PSFS is also an option on the Linux cluster instead of GFS but it's not free. Read more on it [here]("http://h18006.www1.hp.com/products/storage/software/polyserve/support/hp_polyserve.html").

Hope I have not confused you here. If you want to read up on how Windows does clustering, see [http://technet.microsoft.com/en-us/library/cc739634.aspx]("http://technet.microsoft.com/en-us/library/cc739634.aspx")

Cheers!

---

