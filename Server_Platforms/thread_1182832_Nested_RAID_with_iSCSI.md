---
title: "Nested RAID with iSCSI"
date: 2009-06-09
forum: Server Platforms
---

### Post by Grain on 2009-06-09
Hi there, I'm planning on making a nested RAID solution RAID51  utilizing iSCSI as part of the implementation. 

I will have available to me 2 HP DL360 G5 machines, each has 6 drive bays, populated with 146GB SAS drives.  Both of these machines are hardware RAID capable and will be configured with RAID5 arrays on them.  Now I want to use Linux and utilize iSCSI and software RAID to join the two machines together in a RAID1 array, thus making the whole setup RAID 51. 

The final resulting volume would then be shared, potentially to a virtual machine host, or even to several vm hosts.

I'd like to do this with just the two servers if at all possible, as shown in the diagram below. 
```
            
|Dl360|           | DL360|
| hR5 |---iSCSI-->|iS hR5|
                  | \sR1/|
                      |
                     NFS share------>

```As opposed to this, which is a three server solution.

```
            
           |Dl360 |
   -iSCSI->|iS  iS|<-iSCSI-
   |       | \sR1/|       |
|Dl360|        |       |DL360|
| hR5 |        |       | hR5 |
               |
              NFS share------>
                  

```Any advice in setting this all up would be greatlly appreciated.
I should also state that I'm still shopping around for a Linux distro,  is Ununtu right for me. I'm also looking at Cent and Suse.

---

### Post by Grain on 2009-06-11
So... anyone?

---

### Post by PilotJLR on 2009-06-16
Although this would work, I think DRDB would be right up your alley:
[http://www.drbd.org/](http://www.drbd.org/)

And if you're open to using iSCSI for host attachment, instead of NFS, then consider:
[https://help.ubuntu.com/community/HighlyAvailableiSCSITarget](https://help.ubuntu.com/community/HighlyAvailableiSCSITarget)


Pros and cons to both. One nice thing with NFS datastores on ESX is that vmdk's are thinly allocated.

---

### Post by syadnom on 2009-09-11
To have a completely redundany, synchronos setup you need 3 machines.  The raid1 will have to run somewhere other than the 2 storage nodes.  

You could do the raid1 on one of the storage nodes but then you are not redundant because if that node fails all storage is gone.

a 3 machine setup is your best bet.

If you are planning on doing some virtualization you can use the VM management machine as the raid1 host and use iscsi or aoe to get the block devices over
```

storage1->iscsi    storage2->iscsi
            |                  |
            |                  |
             \                /
              \              /
               \->raid1sys--/
(/dev/sde, /dev/sdf = /dev/md0 raid1
                 -or-
 /dev/etherd/0.1, /dev/etherd0.2 = /dev/md0 raid1)
                     |
                  /dev/md0
                export NFS/iSCSI/AoE/Cifs etc


```

as far as shopping around I would suggest to you just 2 distro.  ubuntu, debian, centos5.3(redhat el5.3).  Ubuntu is so simple to setup AoE and iScsi as everything is provided in the repos so for ease of setup ubuntu is king.  debian is very very similar also, but the community is not as helpful.

Also, I would suggest that you either put a dedicated NIC in for storage or at the very least do some VLAN work.

---

