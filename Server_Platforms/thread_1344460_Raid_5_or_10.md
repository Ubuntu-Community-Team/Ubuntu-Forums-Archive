---
title: "Raid 5 or 10"
date: 2009-12-03
forum: Server Platforms
---

### Post by kwickcut on 2009-12-03
i have installed ubuntu 9.10 

server setup

Ausu A8N32-SLI Deluxe

Amd 4200 dual core

4 gigs ocz pc 4000 ram

4 250 gig sata2 hd

[SIZE=2]nvida card
[/SIZE] [SIZE=1][SIZE=2]
ram coolers

5- 120mm fans

2- 80mm fans

this is a good beginners setup i think for a started server..

question is i have the server up and running and ready to host on one 250 gig hd is there a way to convert the system to raid 5 or 10 without reinstalling the hole system



thanks


kwick [/SIZE]         
[/SIZE]

---

### Post by munky99999 on 2009-12-03
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Lars Noodén on 2009-12-04
> **kwickcut said:**
> 
question is i have the server up and running and ready to host on one 250 gig hd is there a way to convert the system to raid 5 or 10 without reinstalling the hole system


You'll need a set of partitions, one per physical disk, to use for the RAID array.  You can use gparted to resize your existing filesystem and grab some of the free space.  Or you can try a live CD and do that.  
It's not hard, but I would plan to rebuild the system anyway.  A lot can go wrong when one is learning repartitioning.  At least do a full backup first.  

The raid tool for Ubuntu would be **mdadm** or a graphical front-end.  Stay away from FakeRAID as it is is unsupported, among other problems.
The software raid HowTo is here:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

To oversimplify, RAID 10 gives you speed at the cost of space, RAID 5 gives you space at the cost of speed.  Neither are substitutes for having a backup, they just provide expanded storage and help you get running again when an individual disk fails.
[http://weblogs.sqlteam.com/billg/archive/2007/06/18/RAID-10-vs.-RAID-5-Performance.aspx](http://weblogs.sqlteam.com/billg/archive/2007/06/18/RAID-10-vs.-RAID-5-Performance.aspx)

---

