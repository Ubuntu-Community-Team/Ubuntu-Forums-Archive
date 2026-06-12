---
title: "DRBD&gt;Corosync&gt;Pacemaker&gt;KVM&gt;Samba question"
date: 2010-10-01
forum: Server Platforms
---

### Post by toshko3 on 2010-10-01
Hi, did anybody make such a configuration for high availability of the Samba server (or another): Ubuntu server>DRBD>Corosync>Pacemaker>KVM>Ubuntu server>Samba with 2 servers/nodes? The point is not to rely on Pacemaker to bring up the samba service on the another machine, but only the virtal machine. So I can replicate the virtual machine file only with drbd and rely on Pacemaker to bring it up on the backup server if the primary failed. 
This way I would not need to rely on Pacemaker for all of the services (incl. samba) and make symbolic links, update the machines equally and so on with all the maintenance needed for the services to work properly. This way when the virtual machine's iso file is replicated - I only need to modify the virtual machine on the primary server.

Another question is worrying me too. The DRBD daemon is working in Synchronous mode. So I assume the following - when a client is writing a file to the server - the file will be written out (from the client's point of view) only when the file is replicated by drbd on the secondary server. So when I use a virtual machine (on which i will run samba), when there are more people simultaneously writing files, the drbd daemon will see only one file changing - the virtual machine file. So will everybody (every samba client) need to wait for the drbd to replicate the whole iso (the file of the virtual machine) file (including the last file from the last samba client), to be answered with success write? 

If this is so, I assume such a configuration is not appropriate (Ubuntu server>DRBD>Corosync>Pacemaker>KVM>Ubuntu server>Samba). The appropriate might will be without the virtual machine. But then there is so much maintenance needed for both of the machines equally for the pacemaker to run all the services. I believe there is a way...:confused:

---

### Post by a9k3d on 2010-10-02
DRBD is low level. It is like RAID1. 
So in your example, if a file is changes on the main SAMBA server and only 5 disk block are written then only 5 blocks need to be written to the secondary samba server.

I configured something like your want. 2 machine with RAID1 and DRBD primary->secondary. I used heartbeat originally but now if we have to switch over we will do it manually. Note that each server has a dedicated IP for ssh access and a "hot" IP that moves with the service.

Good Luck. It is not a trivial setup.

---

### Post by toshko3 on 2010-10-03
Yes but if two samba clients write files simultaneously, the first lets say - 5MB, the second 5GB? DRBD sees block changes of the host operating system's file system (the kvm image file), so when both of them are ready, only then will the first (5MB) be answered with "Yes the file is writen". Am I right?

---

