---
title: "re add lvm2 volumes whiteout loosing data"
date: 2016-07-18
forum: Server Platforms
---

### Post by do.marmor on 2016-07-18
i got a [COLOR=#000000][FONT=Arial]Quad core 2,5GHZ 8GB DDR3[/FONT][/COLOR] running ubuntu server 16 its mainly used as a combined file share/nas for local network and web server for testing purposes seeing i building sites sometimes for others however i got a lot of future plans for this server , that i never had the time to make real yet, The nas part is a set of hard drives set up with lvm2 however the root drive got the partitions like normal meaning not lvm.

Now to my problem, the root drive kinda got a will of its own lately weird enough it passes true smart but Ata error log show [COLOR=#ff0000]1741 errors detected [/COLOR]and running hours 2years 5 months and 16 daysso i think its time to replace that drive. i was first thinking about cloning the drive but now im thinking about doing a fresh install, and install the os with lvm this time, backing up the setup first of course, 
So in the new system i will have two Volume Groups one for the system and one for the local network nas part

My question is simple, can i re add my present lvm logical volumes to a new system whiteout loosing data?

i allso have hell getting php mail to work, but will make new post about that, if i do not get it to work on new setup

---

### Post by darkod on 2016-07-18
From what I understood you do not have LVM right now, but you wish to install it. So is the question about this "migration" of data or the next one?

Anyway, the answer is YES. You can easily re-add existing LVM. Of course, provided you do not format or destroy the partitions on the disks, etc... LVM is easy to re-add. Even ubuntu live mode (live cd in Try Ubuntu) can read existing LVM from the disks. You can use that for example for rescuing data...

---

### Post by do.marmor on 2016-07-19
Ty darkod i think this answer my question

i both have and not have lvm, the system is not set up with lvm but i got one 2 TB drive set up in lvm in its own volume group (plan to add more drives later) this works as the local file share / backup , a nas in other words

so what im trying to is seeing the os drive is in such a bad shape, and i regret not installing the system with lvm from beginning, im thinking about, instead of cloning the os drive , do a fresh install and install Ubuntu with lvm so i can easy move partitions in the future and also have the benefit of snapshot the system before experimenting with something new and of course adding more drives if i need it. only down side i see in this is do all the settings again, luckly i got that on backup
after i done re add the 2 tb drive that is set up with lvm today whiteout losing data on it

so this should not be a problem as long as i dont touch the 2 TB drive if i understand u corectly

---

### Post by darkod on 2016-07-19
If I'm not mistaken the ubuntu server installer might detect the existing LVM and offer to activate it. Even if you say Yes, it doesn't create a mount point automatically for you.

So what you can do, is do the OS install creating new LVs on the OS disk for root, swap, etc, and then you don't even need to create mount point for the data LV at that moment. You can do that later after you have the OS installed.

The main thing is like you said, do not destroy or repartition the partitions on the 2TB disk in any way... Leave it alone.

---

