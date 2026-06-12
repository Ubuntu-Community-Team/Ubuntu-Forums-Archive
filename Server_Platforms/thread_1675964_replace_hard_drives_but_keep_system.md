---
title: "replace hard drives but keep system"
date: 2011-01-26
forum: Server Platforms
---

### Post by skrite on 2011-01-26
Hey all.

Our company just bought faster hard drives for our webserver.
A lot of the software and services set up on this machine have had config files set up, etc.. It would take a while to rebuild it from scratch, which i may have to do. 
I know most config files are in /etc and i can use apt to spit out a list of installed packages. 

Any tips that i may want to know to avoid any gotchas here? We need to minimize downtime, of course, and get everything up like it is now. 

thanks for any tips that might help

---

### Post by arrrghhh on 2011-01-26
Well in theory you could do it with 0 downtime if you have a RAID array.  I don't think that's the intended purpose, but it would probably work.

If not, you'll need to backup everything to the new hdd's and replace them - not terrible for downtime, but there will be some.  Assuming you do a bit-for-bit copy, the new hdd should just drop in and go.

---

### Post by sikander3786 on 2011-01-26
I would recommend considering Clonezilla. You can clone your entire disk to the new one's over the network or from HDD to HDD.

[http://clonezilla.org](http://clonezilla.org)

---

### Post by crashed111 on 2011-01-26
I agree with the above Clonezilla is really easy to use. 

You can also use it to make a disk image as a backup so you can restore from this if the disk ever did fail.

---

### Post by koenn on 2011-01-26
clonezilla would work, but takes time. your system will probably have to be down during the time it takes to clone the disks.

I'd just attach the new disks to the computer, copy all the necassary stuff (dd, rsync, cp, ... ),  then take out the old disks and boot the system with the new disks. Or at least see if it boots. 
Expect to have to fix grub and fstab (getting the GUIDs from the new disks might be a good idea)

the feasibility depends a bit on just hao many disks we're talking about, extra complexity because of lvm or raid, the amount of data and etc

The good thing about this is that the system can stay up while doing the copying (you may have to rsync the data again afterwards) so downtime is minimal, and you can plan for that. 
If it doesn't work, roll back by putting back the old disks; then think about why it didn't work and use that info to plan your next attempt. 

a practise run, eg by swapping disk files in a virtual machine, might be a good idea too.

---

