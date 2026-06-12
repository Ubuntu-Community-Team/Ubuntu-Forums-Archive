---
title: "What are my best options for setting up a cluster?"
date: 2007-01-09
forum: Server Platforms
---

### Post by NaughtyusMaximus on 2007-01-09
I have a need to set up a cluster system so that I can offer high availability for my servers. The hardware I have is as follows:

2 x VMWare servers
2 x 3TB RAID arrays (Promise VTrak M210p )

The SCSI RAID arrays are external enclosures which hold 8 drives. Array 1 is attached to Server 1, and Array 2 is attached to Server 2. Ideally I would like Array 2 to be an identical copy of Array 1. I don't know if this is the best option, as I could also directly connect both Server 1 and Server 2 directly to both Array 1 and Array 2.

The end goal I would like is to be able to disconnect any one of the components of the system and still have my users able to work as normal. For example if 5 hard drives in Array 1 were to die at once, I want my users to be able to keep working, but in the background everything should be working on Array 2. Repeat for each of the components...

I will be doing the clustering at the Virtual Machine level, where each server will have at a VMWare client machine running Linux and several applications which require access to the RAID Array. So if I have VMWare Client 1 on Server 1, I would like it to be in a cluster with VMWare Client 2 on Server 2, and so on.

I've read several articles on open source clustering options, and am still confused as to whether or not what I want to do is possible (or whether this is even popular). From what I can tell my best course of action is to use OpenMosix, but I could really use some advice as to how I should best proceed in setting up the above system.

Thank you for any help you can offer

---

### Post by PilotJLR on 2007-01-09
The direct attached storage could be a problem... with several terabytes, this really, really should be iSCSI at least or FC at best.
With 2 separate DAS units, you'll have to replicate between them, so the servers would probably have to act as middle-man... with an iSCSI san, for example, the SAN itself can be configured for replication.

Of course, if you have such a setup, then Vmware VI3 would allow you to cluster and migrate VM's, which would accomplish what you are looking for.
One thing you CANNOT do with this setup is HA, where VM's on a failed ESX are migrated and restarted. That feature absolutely requires FC.

Sorry though - with the hardware you have, the replication is doable, but I'm not aware of a way to cluster the VM's using DAS.

---

### Post by NaughtyusMaximus on 2007-01-11
"Sorry though - with the hardware you have, the replication is doable"
Any suggestions for how to do this?

---

### Post by NaughtyusMaximus on 2007-01-12
Would it make sense for me to connect my RAID arrays to a separate RAID controller, and mirror them at that level?

I'm not sure if this is possible (I think it should be), but from what you're telling me it would make things a lot easier to deal with.

---

### Post by PilotJLR on 2007-01-12
> **NaughtyusMaximus said:**
> Would it make sense for me to connect my RAID arrays to a separate RAID controller, and mirror them at that level?

I'm not sure if this is possible (I think it should be), but from what you're telling me it would make things a lot easier to deal with.

With a high end RAID card, I think this is possible... but the problem there would be that only 1 server would have it directly attached... the other server would need to use NAS.

For not quite real time mirroring, rsync is easy and effective:
[http://sunsite.dk/info/guides/rsync/rsync-mirroring.html](http://sunsite.dk/info/guides/rsync/rsync-mirroring.html)

For REAL real time mirroring, which would provide a form of clustering (but be much harder to setup), I found this:
[http://www.drbd.org/](http://www.drbd.org/)
fyi, i have not used this item, but it looks good on the surface.

---

### Post by NaughtyusMaximus on 2007-01-16
I've been doing some more research, and I'm trying to figure out if RedHat's GFS might be applied to my situation. Again in the docs, I'm finding it hard to tell whether GFS has been designed with redundant data stores in mind. Different things in the docs make me think both that it will work and that it will not...

GFS was (at least) designed with the idea that each server will be directly connected to the data store, which is what I will be doing. That at least is hopeful. I am downloading a CentOS CD right now to see if I can determine the answers to my questions by playing with the software itself. If anyone knows offhand if GFS and RedHat's clustering management might be a good fit for me, I'd appreciate any input.

DRBD also looks like a promising alternative, my worry with it is that if I want to have each server responsible for a single task (DB, SMB, NFS, etc.), I'm under the impression that I will have to make a fixed partition size for each of these servers, and will be unable to have them all access the same total pool. Is this correct?

---

### Post by PilotJLR on 2007-01-16
I'm pretty sure the RH Cluster Suite is for active/passive clusters (but I could be wrong).

GFS is just a cluster filesystem... which enables multiple servers to write to SAN.

---

### Post by sunmouse on 2007-05-10
VMWARE ESX Server allow you to create a Active/Active Cluster. Move Virtual Machine wile they are up and to manage your whole environment.

---

### Post by PilotJLR on 2007-05-10
No, that's not correct.

ESX allows for no load balancing whatsoever. VMotion (moving VM's like you mention) is a features for portability and maintenance. Even with DRS, resources are never shared between physical hosts concurrently.

ESX / VI3 has a "high availability" feature, but that merely restarts VM's after a host fails. There is still downtime, so it's not a real cluster.


Only true clustering (like Cluster Suite) offers a possibility of a 100% uptime (everything outside the rack excluded).

---

### Post by rohix on 2007-08-14
I also have similar setup. What would be the best solution? GFS?

---

### Post by PilotJLR on 2007-08-14
Red Hat Cluster Suite with GFS shared storage is the only way I know of making a "real" cluster in Linux. (except for HPC stuff like Beowulf)

---

