---
title: "Cannot login, need fresh start (reformat two hard drives)"
date: 2010-04-06
forum: Server Platforms
---

### Post by cK` on 2010-04-06
Hey, i am 100% nooby.

I recently acquired a server with two hard drives.

I installed unbuntu server edition. Being the noob that i am and for reasons i dont care to explain i installed the OS on BOTH hard drives. But on top of that one of the installs did not complete. 

This is causing me some problems, 

the biggest one being i can no longer login to any of them :lolflag:

I would like to clear both hard drives of unbuntu server and start over fresh with nothing on either hard drive 

then i would like to reinstall Unbuntu server with my burned bootable cd on one of the hard drives and use the other one for free space.


Partitioning the second hard drive is not really that important ATM, right now i just want to get Unbuntu server running again :popcorn:

Any help is much appreciated

P.S: I burned gparted onto a disc but i have no idea how to use it, i could only find tutorials about the desktop edition not server.



Thank you!

---

### Post by richardjh on 2010-04-06
Just boot off of the Ubuntu CD and work through the steps. When it comes to disk partitioning you can opt to blow away you current partitions and start again. You don't need to use any other tools.

You will need to customise you partition layout to use two disks, I would suggest allowing the partitioner to determine the best layout for the first disk and then choose to format the second drive as ext3 and set the mount point to something like /data to keep it simple.

---

### Post by cK` on 2010-04-06
Ok thanks all read up on how to customize my partitions.

---

### Post by romeroc24 on 2010-04-06
Yeah man, the partitions are important, install file systems on / with ext3 and use all disk, if you want try to use a swap partition too for use it like virtual memory.

---

### Post by cK` on 2010-04-07
Thanks i think i got done what i need to do.

But i dont think its running like it used for example when i try and use nano to edit files it lags so much its almost unusable, i have to reboot my server to get it to work right, also i cant install webmin correctly even though i am doing exactly when i successfully installed it.

---

