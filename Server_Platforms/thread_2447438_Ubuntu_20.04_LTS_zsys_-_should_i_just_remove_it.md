---
title: "Ubuntu 20.04 LTS zsys - should i just remove it?"
date: 2020-07-18
forum: Server Platforms
---

### Post by notanothersignup on 2020-07-18
Server is a recent install with xen and zfs. There is very little installed on Dom0 and zfs setup is essentially as per ubuntu scripts from the openzfs ubuntu 20.04 page. Zfs is working fine but zsys has already started to play up after a few days. It's making me a bit nervous with the things it's logging, massive timeouts and zsysd seems totally broken at this point. I did disable the user snapshot as it seemed pointless, not sure why that would cause issues though. I also have zfsnap setup. I get the impression that zsys breaks when there are snapshots that it didn't make present (looks like there could be a similar issue with docker generated snapshots). This is what's worrying me, i.e. is it going to start deleting things it doesn't own and what would happen if I did ever try and restore using the grub menu option. Would I end up with a broken system, snapshots / backups etc. I'm not sure I want to do a restore and find it's done a random rollback on some other part of the system I didn't want without warning. I'm also replicating rpool to another pool so I can keep more snapshots there but it looks like zsys is picking them up and not entirely sure if that is going to cause problems (or is part of the cause of zsys breaking - but that doesn't give me any confidence if it isn't even tested with a backup pool).

There seems to be a large amount of syslog messages similar to the following for every snapshot including the autozsys snapshots on the backup...

zsysd[3085100]: level=warning msg="Didn't find origin .....
zsysd[3085100]: level=warning msg="Couldn't find any association for user dataset .....

I obviously still need everything mounted at startup and I guess I'd like to be sure whether the zsys package can be safely removed or if I'm going to get boot issues. I can manually disable the apt hooks and services if removing the package is a problem.

Did anyone else run into issues?
Are people running zsys on server with user managed snapshots and has anyone ever tested the rollback function?

---

### Post by Sithuk on 2020-07-21
I have the same problem. The logs are full of:
"ubuntu zsysd[713993]: level=warning msg="Didn't find origin...

I'm running zsys version 0.4.6, zfs version 0.8.3, and ubuntu 20.04.

---

### Post by Sithuk on 2020-07-23
This zsys issue report might be relevant.
[https://github.com/ubuntu/zsys/issues/103](https://github.com/ubuntu/zsys/issues/103)

---

### Post by Sithuk on 2020-07-23
Could also be related to the bug described here (fix due in 0.4.7).
[https://github.com/ubuntu/zsys/issues/156](https://github.com/ubuntu/zsys/issues/156)

---

### Post by dad+sithlord on 2020-12-29
> **notanothersignup said:**
> 
...
Are people running zsys on server with user managed snapshots and has anyone ever tested the rollback function?
  
The zsys authors have published a set of blogs covering various aspects of zsys, including where use of xen/docker/virtualbox or other hypervisors that manage their own data sets (snapshots etc) is concerned.  
A set of blogs covering zsys were published May/June of 2020.  This link details aspects relating to docker etc:
[https://didrocks.fr/2020/06/16/zfs-focus-on-ubuntu-20.04-lts-zsys-dataset-layout/](https://didrocks.fr/2020/06/16/zfs-focus-on-ubuntu-20.04-lts-zsys-dataset-layout/) 

zsys uses properties within ZFS to identify which it should look after.  This also allows for "Persistent data sets" - those NOT managed by zsys (because something else does, like docker or xen).
The data sets can be seen with the command
zsysctl show --full

by default you will see on the Ubuntu Desktop:
Persistent data sets: None

zsys creates the snapshots within rpool and pool, combining them into "states".  These states are managed, including the rpool/USERDATA area.  The default zsys settings for snapshots and creating these "states" are managed by a reasonable set of policies (that can be modified), but the persistent data sets are NOT snapshot and will not be rolled back with the rest of the system.  From the blog post referenced above:
> 
We [authors of zsys] have thus a lot of dataset (which is basically no cost, just more  code in how we have to handle it) on the desktop, but this brings this  whole flexible where sysadmin can switch between types with a simple zfs  rename.


For others setting up servers see [https://didrocks.fr/2020/06/09/zfs-focus-on-ubuntu-20.04-lts-zsys-for-system-administrators/](https://didrocks.fr/2020/06/09/zfs-focus-on-ubuntu-20.04-lts-zsys-for-system-administrators/) and the other blogs first.

Hope this helps, especially others looking at this.

---

