---
title: "LVM: Multiple partitions across HDDs?"
date: 2011-11-01
forum: Server Platforms
---

### Post by Howy on 2011-11-01
Ok, so we're running a homeserver. It's nicely running, and all the services work as they should. The only problem is storage. It has a 250Gb HDD at the moment, where 200Gb are allocated as server storage and 50Gb for the root filesystem. (Just to avoid crash in case of too little memory. Less worries.)
In the setup process (Ubuntu Server 10.04) I set up LVM. I assume that this makes space allocation easier, but I'm not 100% sure how to manage it.
We're planning to purchase a new HDD, possibly a 2Tb one that'll hold for a long time. (And possibly extending from that in the future just for the lolz)
I'm wondering, would it be possible to make this HDD work seamlessly with the existing one? I mean it so that the logical volumes span across the HDDs.
Is this possible? And if so, how would I do this?

---

### Post by vasile002 on 2011-11-01
you can't do it without RAID

why would you need it anyway? you can just mount the new drive separately

---

### Post by Howy on 2011-11-01
The thing is that I have 1 folder mounted as a media folder through Samba. I only want to extend the storage available in that folder, without segmenting the media in any way across different drives.
It would be inconvenient in cases like if there is a lot of pictures or music that it ran out of space.
But if I do use RAID, will I be able to simply extend, or only mirror the drive?

---

### Post by FunkyMinky on 2011-11-01
If you are using LVM for the shared directories it is quite possible to add another drive, add it into the LVM pool and expand your current directories.

It's a bit fiddly to begin with but theres a few readme's out there.
One caveat is that you can't shrink partitions once you've expanded them (at least not easily).

In essence you will do a pvcreate on your new drive (find drive with fdisk -l)
Then vgextend your existing volume group(s) with this new drive
unmount the current logical volume you wish to expand
lvextend your logical volume (the partition/share you wish to expand)
then do a resize2fs to expand the underlying filesystem to match the logical one in size.
Re-mount and you should be good to go.

---

### Post by Howy on 2011-11-01
Question: If I've understood the theory behind LVM, it's so that I can extend it all on-the-fly?

I just wonder about something. I've set up the Udisk TCP bridge, so that I have access to the partitions of the server on this desktop. I see that it has an option to make RAID-0. Would I get away easily with that, or am I bound to go the hard way? I've got some really bad experiences when it comes to low-level partition tools. (Messed up in a VM once. Unrecoverable damages to the partition table.)

---

### Post by darkod on 2011-11-01
1. The point of LVM is that you can easily add new physical devices (disks) and expand the logical volume to include them, without formatting (losing data).

2. When setting up RAID of any level (and this includes RAID0) the point is that the disks get formatted during the creation of the array. So there is no way to do it without data loss (or having to move the data elsewhere, create the array and move it back). At least not as far as I know. This includes both software raid and fakeraid (mobo bios raid). When creating an array the partitions/disks get formatted as raid type, only after that you create ext4, ntfs, etc partitions onto the raid device.

PS. Another point to consider is that almost all raid types require disks/partitions of equal size. If any disk is bigger the rest of the space is usable outside the array, or not, depending of the setup. If I got it right, if you use softraid you first make partitions, and then the OS is creating an array from them on partition level. That means you can use the rest of any bigger disks but outside the array.
Fakeraid will just use the part of the bigger disk and the rest is unusable.

With having 250GB and 2TB disks, planning any type of raid is pointless. The best you could make is a software RAID0 of 2 x 250GB and the rest 1.75TB as simple unraid partition. Will it be worth it? Plus, RAID0 is one of the worst, the data is written in turns on both disks, without redundancy. If one disk fails, you lose all the data because the other disk will have just half of it, you can't restore it from that.

---

### Post by koenn on 2011-11-02
> **Howy said:**
>   ... 
so that the logical volumes span across the HDDs.
Is this possible? And if so, how would I do this?

here's a short introduction to LVM

[http://users.telenet.be/mydotcom/howto/linux/disks2.htm](http://users.telenet.be/mydotcom/howto/linux/disks2.htm)

---

### Post by Howy on 2011-11-02
Ok, I think I got this.
I'll do a pvcreate on the partition.
Then I do a vgextend to make the logical group span it.
I then do a lvextend to take up all that space, and finally format the space with ext4.
Would this successfully do it?
If so, it looks quite simple and easy to do in the future. :)
Thanks for tip, koenn.

darkod, I see. I see that I thought of RAID the wrong way. Thanks for the enlightenment.

---

### Post by darkod on 2011-11-02
After the lvextend your new partition(disk) will be included in the logical volume. You do not specifically do ext4 formatting.
Later when expanding any partition onto the available logical volume space, it takes care of the formatting automatically. You simply expand the partition and the system sorts out everything for you.

This is rather old but extensive LVM guide (note that it also has instructions for LVM1 and the newer LVM2 now in use):
[http://www.tldp.org/HOWTO/LVM-HOWTO/index.html](http://www.tldp.org/HOWTO/LVM-HOWTO/index.html)

Look in section 11 that covers exactly the operations you want.

---

