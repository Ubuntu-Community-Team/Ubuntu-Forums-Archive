---
title: "raid to windows virtualisation?"
date: 2011-10-21
forum: Server Platforms
---

### Post by Error403 on 2011-10-21
Hi there,

I'm trying to find an economic way to have loads and loads of hard drive storage space for a windows installation..  Could it be possible to RAID5/6 a bunch of 2TB drives and pass it as a humoungus single drive to a virtual Windows installation?  I'm pretty new at this so I might miss a few points  ;)

---

### Post by newbie-user on 2011-10-21
If your goal is simply loads and loads of hard drive storage, then you might want to consider logical volume management instead of RAID 5/6.  In RAID 5/6, you'd actually lose some physical storage space due to parity data.

Otherwise, you could span a logical volume in Windows across an entire RAID 5/6 array if you wanted to.

---

### Post by Error403 on 2011-10-21
Well maybe I asked too fast...  I meant loads and loads of hard drive space with a minimum of data security / redudancy in case one or more hard drives fail. Last time I played with LVM if a drive went down the whole thing went with it.

---

### Post by newbie-user on 2011-10-21
Okay, then RAID 5/6 would be better.  We have a RAID 5 setup on one of our servers and it just looks like one big drive.  Just set up the RAID before you install Windows and you're good to go.

You mentioned economic in your first post.  Are you thinking software RAID or do you already have parts for a hardware RAID?

---

### Post by Error403 on 2011-10-21
For now I'm only thinking of filling a standard pc's pci slots with SATA controler cards and let Linux do the rest. It's gona be ugly at first but I have to start somewhere.

What about growth? Lets say I manage to setup a 10TB RAID5 then next year I want to add a few new drives? Will that be feasible without losing all the data ?

And how will windows see and manage such a huge partition? Will ntfs be able to handle it, or will I have to switch to GPT (whatever that is) ?

---

### Post by newbie-user on 2011-10-21
> **Error403 said:**
> For now I'm only thinking of filling a standard pc's pci slots with SATA controler cards and let Linux do the rest. It's gona be ugly at first but I have to start somewhere.

What about growth? Lets say I manage to setup a 10TB RAID5 then next year I want to add a few new drives? Will that be feasible without losing all the data ?

And how will windows see and manage such a huge partition? Will ntfs be able to handle it, or will I have to switch to GPT (whatever that is) ?

Here's a link to posts on how to grow a RAID5 array.

[http://ubuntuforums.org/archive/index.php/t-517282.html](http://ubuntuforums.org/archive/index.php/t-517282.html)

As for the Windows side of it, NTFS won't have a problem with the large volume size.  GPT stands for GUID Partition Table, which is a newer disk partitioning method that is replacing the MBR, or Master Boot Record.  It's more important to use GPT instead of MBR because MBR will limit you to 2TB volume sizes.

---

### Post by Error403 on 2011-10-21
Thanks, I guess I'll cross that bridge when I'll get to it. You make it sound pretty easy so I'm not worried for now.

---

### Post by Demented ZA on 2011-10-21
>  Could it be possible to RAID5/6 a bunch of 2TB drives and pass it as a  humoungus single drive to a virtual Windows installation?

I'm actually doing this on a headless Ubuntu 11.10 (recently upgraded from 11.04) headless server, using virtualbox for the virtualization. I'm running three WD caviar black 7200 RPM SATA 6G drives. Intel Sandybridge Core i5 2500k CPU and motherboard to match. Also running 4 gigs DDR 3 memory in dual channel.

A couple of months ago (havn't tried it since), the problem I was experiencing is a sort of stuttering when I remote desktop to the windows 7 installation I'm running on it. I'd be working for a while, and then the VM would freeze for some seconds, and then continue again for about a minute before it happens again. When I'm running some applications it gets worse.

Its not lag per se, and its not performance related (ram, cpu) as far as I can tel because according to Ntop, Cpu usage dwindles at ~2%, ram around 30%.

I stopped running the VM and started porting all the functions expected of the machine to native linux.

Its been a year, and plenty of updates (Including VirtualBox) since, and I havn't tried it again, yet. 

Although, I have a hunch the freezes were due to the VM running of the RAID array, so I'm assuming its IO bottlenecks that caused the issue.

I would suggest using a single HDD, not part of the RAID array for the Ubuntu server install, as well as the storage for the Virtual HDD that contains the installation of the Virtual windows, then map the Raid 5 array to this install using Samba or NFS.

---

### Post by SparkyUSN on 2011-10-21
I'm currently messing around with [greyhole]("http://greyhole.net"), which allows you to merge an arbitrary number of drives into a storage pool (like LVM) share virtual drives over samba and specify (per samba share) the number of actual copies (on separate physical disks) that each file on each virtual share is stored as, which gives the redunudancy you are looking for in RAID 5 or 6.

That is, I have the following samba shares:
photos
music
library
videos

Each of the files in photos and videos is stored on two of my four physical drives.  The music and library shares are simplex.

The advantage of this over RAID is that you can add arbitrarily sized drives to the pool (unlike RAID, which will require that each drive appear as the size of the smallest in the pool).  The downside is that the redundancy is not as efficient (double the space for the duplex files).

In my opinion, the greyhole tool is elegant and I'm going to work to make the documentation friendlier to idiots like myself.  I'm interested if you try this solution.

---

### Post by Error403 on 2011-10-21
Demented, Sparky,

Thanks for your input. I'm gona think about those in my strategy.

---

### Post by Vegan on 2011-10-21
I suggest a UEFI based system with a RAID6 card for the best in storage. RAID6 can survive 2 disk failures, but its not a bad idea to have a couple spares in a box just in case.

SAMBA can share an array easily for Windows clients.

NFS is another route for a mixed shop

---

