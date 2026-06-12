---
title: "Ubunt Server LVM + RAID Best Approach"
date: 2013-04-11
forum: Server Platforms
---

### Post by ally_uk on 2013-04-11
Hey Guys I am fairly new to Ubuntu I am in the process of tinkering with LVM I have a server with two identical drives 160GB my partitioning scheme isn't fancy it is basically used as a way of learning about how LVM works.

/boot - 300MB not part of the VG
/109G
/home120G


So far both disks are being used in the LVG ( I used the second disk to extend the Logical Volumes. Now I have LVM setup I was thinking of taking things further and setting up some form of Redundancy with the inclusion of RAD-1 on both disks. Firstly is this the best approach is it considered good practice to run LVM with Raid? 

what's the procedure for setting up mdadm with LVM or should I of configured mdadm first?

Keen to learn appreciate the feedback :)

---

### Post by darkod on 2013-04-11
Yeap, mdadm raid first. So, in fact it would be more correct to say RAID + LVM. :)

I guess it would go like this:
1. You make small 500MB or 1GB partitions at the front of the disks, to later make raid1 device from them for /boot (so that it can be outside the LVM). Lets call it /dev/md0.
2. Then you make big partition from the rest of the disks, and make a bigger raid1 device from them. Lets call it /dev/md1.

Then, you use /dev/md1 as the physical device for the LVM, and you configure it like you did last time. You obviously know how to do that.
You use the /dev/md0 for /boot.
That's it.

Basically, the line of thought is: The mdadm raid is mirroring the data on both disks, it doesn't really care what's on the disks. once you have the large array set up, you can use it as physical device for LVM, set up the VG and the LVs you want. That's about it...

If at any time one disk fails and you replace it with a new one, mdadm will sync it to the existing disk not caring that LVM is running on top of the raid.

---

### Post by ally_uk on 2013-04-11
Ok Thank you for the heads up I have decided to start again with the installation but need a few things clearing up

I will be using two 160GB SATA Hard Disks for this install SDA, SDB

Ok first question is during the install do I first need to setup the partitions i.e /boot, / /Home or do I just use all of the space of SDA and select use as Raid do the same for SDB and create the Raid 1 Mirror

Second Question /boot on a separate partition?

Once the Array has been created do I then configure the partitions to be use for LVM? this doesn't make sense because if I have already created partitions earlier they would of been set to use Kraid.

Last once the LVM has been creating and we have the raid 1 mirror setup on both drives if I was to run out of space in the VG would I be able to whack in another drive and extend? how would the raid work? 


:0 Think I am confusing myself with the two drives how would you go about this?

---

### Post by darkod on 2013-04-11
You got most of it right, except one important thing about mdadm. If you want a mount point outside the array (like for /boot), you need more than one mdadm partition. This is because each mount point needs separate md device.

Also, I have no idea whether putting swap inside the LVM is better or worse, you might as well make two identical partitions on the disks and use them for swap directly, unreaided and outside the LVM.

In that case, each of the 160GB disks would look like:
Partition #1 - 1GB for raid
Partition #2 - xxxGB for raid
Partition #3 - 2GB, swap area

After you create those partitions and they show up in the list, go into the Configure Software Raid option. Make /dev/md0 from sda1 and sdb1, and /dev/md1 from sda2 and sdb2. Don't forget, you don't need to raid swap.

That will make the two md (raid) devices show up in the partitions list too.

Select md0 and in Use As select ext4. Mount point /boot.
Then select md1 and in Use As select Physical device for LVM.
You selected swap area for sda3 and sdb3 while creating them, so they will be used for swap automatically.

After you are back to the partitions list, now go into the option Configure LVM and use the md1 device to create your VG and the LVs you want. As minimum, you need a root LV, other if you wish.

When all the LVs show up in the list, select them one by one, Use As ext4, mount point depending on how you want to use the LV.

One note, when selecting LV size do not allocate all space from the VG right away. The point of LVM is that you can start with small LVs and expand them dynamically as you need in the future. You rarely know the size from the start, if you do you can make fixed partitions and not use LVM at all. So, make the LVs small, just enough to hold the data for their role, for example you can start with 15GB for the root LV. You can always expand any LV later but shrinking is more complicated (though not impossible). That's why it's better to start small.

After you are done with the filesystem and mount points for each LV, you are done. Continue the install and that's it.

---

### Post by ally_uk on 2013-04-11
Fantastic explanation :) I'm printing this for reference ever considered becoming a ubuntu trainer? Awesome stuff thank you

---

### Post by RATSSWFL on 2013-05-29
First, this thread has helped to clarify a lot of conflicting  information I've seen on the use of RAID on the Boot/OS drive.  Thank  you very much.

It has brought up one additional question,  however.  In the 3 partitions scenario, how is the unRAIDed Swap  partition treated during failed drive replacement/rebuild?  Is it simply  be ignored and left unallocated?  If so, and if the idea behind doing  this to begin with is that you "pop in a new drive and everything just  keeps working", wouldn't that be defeating the purpose?

I'm  coming to Ubuntu Server from a ReadyNAS Duo, and I gotta say that the  fact EVERYTHING is rebuilt, not just the data, is a huge convenience.

Of course it's also possible that I'm completely missing the point.

---

### Post by redmk2 on 2013-05-29
> **RATSSWFL said:**
> ... Of course it's also possible that I'm completely missing the point.

It may well be.  But then again, the water is pretty murky anyway.  Both RAID and LVM provide striping for high availability.  I'm not so sure that there is much practical difference when using either on small disk arrays.  I don't see the need to use both LVM and RAID on the same disks.  Both are abstraction layers between the disk (HDD) and the partition with the file system (i.e EXT4).  Both methods were/are more concerned about how to manage "spindles" (an entire disk) rather than managing partitions in the end.

I prefer the flexibility of LVM myself.  The main point for RAID to protect against disk (spindle) failure and subsequent replacement.  At the present time large disk data recovery is problematic with RAID so I don't see any advantage with RAID.  See [**[COLOR="#FF8C00"]here[/COLOR]**]("http://storagemojo.com/2012/07/23/the-post-raid-era-has-begun/") for more info.

In no way should you consider RAID as a method to protect your data.  If your data is important to you then back it up to a separate host.

[COLOR="#0000FF"]Edit:  Answering your swap question; The swap area is a partition that is allocated but not mounted.  This is usually on the disk that the root (/) partition (and file system) resides.  Whatever happens to that disk will affect the swap area. [/COLOR]

---

### Post by RATSSWFL on 2013-05-29
For my own application, data (the stuff I wanna share with my family) will live in a 4 disk RAIDZ2 array on a seperate SATA controller.  But that's a discussion for another thread on another day.

My interest here is to eliminate downtime and the need to reinstall the OS, so spindle failure is EXACTLY the concern.  It seems to me that the explanation in this thread would accomplish that, but only if ALL partitions are included.  If a drive fails, the system simply moves on without it until it is replaced, at which point a COMPLETE mirror rebuild takes place.

---

