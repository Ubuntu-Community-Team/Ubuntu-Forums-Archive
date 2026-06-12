---
title: "RAID 10 implementation"
date: 2008-04-29
forum: Server Platforms
---

### Post by TheGameAh on 2008-04-29
Hi guys.  Looking for some pointers here.

Trying to create a RAID10 file server, auxiliary storage really.

This is probably just a really stupid problem on my end, but can't figure it out for the life of me.  Seams like basic RAID management really.

4 disks.  All identically partitioned.

100 MB /boot, RAID1 with 2 spares (I hear you can't use RAID10 for /boot)
2 GB swap on each disk (not mirrored)
remainder of disk is /, RAID10

Everything installed fine.

So I remove a disk just to see what happens.  Just testing everything really.

And the system can't boot.  MDADM says it doesn't have enough drives to start the array.  Well, obviously, I failed one on purpose.  Shouldn't the system boot anyway?  Isn't that the point of having a RAID, in case a drive fails?

---

### Post by adamitj on 2008-04-29
I'm not sure, but I think the clusters deployed with MDADM needs the original number of disks to work, ever. Only RAID 1 can work without the exactly number of disks AFAIK.

Try to start the RAID cluster and save a file. Remove one disk and format it. Then put it again on cluster and verify if synchronization is working on it.

---

### Post by ryot on 2008-04-29
Raid 10 should still work after a loss of a drive. You may try booting into the live CD and rebuilding it. After its rebuilt and in the OS, then remove a disk to test it.

---

### Post by mam00th on 2008-04-29
> **TheGameAh said:**
> 
And the system can't boot.  MDADM says it doesn't have enough drives to start the array.  Well, obviously, I failed one on purpose.  Shouldn't the system boot anyway?  Isn't that the point of having a RAID, in case a drive fails?

AFAIK, raid1 wont function if one disk fail neither will raid 0 or 10. RAID5 and possibly raid 6 continue to run if one drive fail.

---

### Post by ryot on 2008-04-29
Here is a good overview of raid arrays.[http://www.acnc.com/04_01_10.html]("http://www.acnc.com/04_01_10.html") Raid 10 has the same fault tolerance as raid 1, which is a mirror. The array will no longer be viable until rebuilt but the data is still there and can be booted as long as grub is installed on that drive.

---

### Post by ryot on 2008-04-29
And also, Raid 0 is the raid implementation that will not tolerate any failures. One drive dies.....all data gone!

---

### Post by keld on 2008-05-11
Raid10 will function in degraded mode if one disk fails.

See the howto on preventing against one failing disk using raid10 at [http://linux-raid.osdl.org/index.php/Preventing_against_a_failing_disk](http://linux-raid.osdl.org/index.php/Preventing_against_a_failing_disk)

---

### Post by songshu on 2008-05-11
your partitioning looks fine.
and RAID 10 should boot, i tested this on Debian Etch extensively detaching all the disks, not all at the the same time offcourse ;)
[http://www.songshu.org/index.php/setup-raid-10](http://www.songshu.org/index.php/setup-raid-10)
this is what i did and this works.

i've also been hearing stories that Hardy RAID 1 has a bug, sounds like exactly the issue, you might just want to team up on launchpad for this

---

### Post by windependence on 2008-05-11
Just curious, why RAID 10? RAID 5 would work much better IMHO. You only need 3 disks to do RAID 5, and you can pull a drive with no problems although the array will be degraded.

-Tim

---

### Post by songshu on 2008-05-11
> **windependence said:**
> Just curious, why RAID 10? RAID 5 would work much better IMHO. You only need 3 disks to do RAID 5, and you can pull a drive with no problems although the array will be degraded.

-Tim

its a matter of dispute oftenly but with raid10 you can actually loose 2 disks (as long as long as its not the wrong 2) so slightly more secure.
at the cost of 50% diskspace instead of 30%

its faster, really it makes a difference (especially with linux raid in my experience)

most real problems with raid5 occure when you actually loose a disk and then need to hotswap, usually a disk that has been on stand by will suddenly be put under a big load and this is where percentage wise the moment things bad can happen to a raid5.

as far as i can tell raid10 will give you a little more performance and slightly more security at the cost of some diskspace and a little flexibility if you would like to increase the array at a later point.

this all providing your distubution of choice would ship without bugs in their mdadm package........

---

### Post by bakegoodz on 2008-08-19
[http://www.howtoforge.net/install-ubuntu-with-software-raid-10](http://www.howtoforge.net/install-ubuntu-with-software-raid-10)

---

### Post by Krupski on 2008-08-19
> **TheGameAh said:**
> Hi guys.  Looking for some pointers here.

Trying to create a RAID10 file server, auxiliary storage really.

This is probably just a really stupid problem on my end, but can't figure it out for the life of me.  Seams like basic RAID management really.

4 disks.  All identically partitioned.

100 MB /boot, RAID1 with 2 spares (I hear you can't use RAID10 for /boot)
2 GB swap on each disk (not mirrored)
remainder of disk is /, RAID10

Everything installed fine.

So I remove a disk just to see what happens.  Just testing everything really.

And the system can't boot.  MDADM says it doesn't have enough drives to start the array.  Well, obviously, I failed one on purpose.  Shouldn't the system boot anyway?  Isn't that the point of having a RAID, in case a drive fails?

Here's what I do... it may be what you need:

I run a file server box with 4 hard drives (1 TB each) setup as RAID 0+1 (2 TB striped and mirrored available). BUT, Ubuntu Server 64 bit 8.04.1 is installed on a SEPARATE Compact Flash card (4 GB) partitioned 2GB for server and 2GB swap space.

The CF card is installed into a CF to IDE adapter card, and that card is plugged directly into the motherboard IDE port (the hard drives are SATA).

So, Ubuntu always boots and runs from a solid state drive... the hard drives are ONLY for data storage. Therefore, the system will always boot, regardless of a RAID disk failure.

Here's the adapter card I use (browse the company's website for different interface options): [**[COLOR="Blue"]_LINK_[/COLOR]**]("http://www.addonics.com/products/flash_memory_reader/adebidecf.asp") 

Hope this helps...

-- Roger

---

### Post by TheGameAh on 2008-08-19
That's a pretty cool idea Krup  :)

I did get all of this working.  Sorry I didn't post back.  The problem ended up being, like was said earlier, a bug in Ubuntu.  Debian works just as I thought it would.  Pull a drive, system still boots.

---

### Post by keld on 2009-01-12
> **Krupski said:**
> Here's what I do... it may be what you need:

I run a file server box with 4 hard drives (1 TB each) setup as RAID 0+1 (2 TB striped and mirrored available). BUT, Ubuntu Server 64 bit 8.04.1 is installed on a SEPARATE Compact Flash card (4 GB) partitioned 2GB for server and 2GB swap space.

The CF card is installed into a CF to IDE adapter card, and that card is plugged directly into the motherboard IDE port (the hard drives are SATA).

So, Ubuntu always boots and runs from a solid state drive... the hard drives are ONLY for data storage. Therefore, the system will always boot, regardless of a RAID disk failure.

Here's the adapter card I use (browse the company's website for different interface options): [**[COLOR="Blue"]_LINK_[/COLOR]**]("http://www.addonics.com/products/flash_memory_reader/adebidecf.asp") 

Hope this helps...

-- Roger

Hmm, why do a RAID 0+1? RAID10,F2 has about double the performance of RAID 0+1 for sequential reads, and is easier to set up.

Also why not have your root and swap on raid? This would improve your performance and chances of surviving a device crash.

I think there may be wear problems with SSD devices. At least some will only take a limited number of writes. There are special software around to help distribute the writes over the SSD to prolong the life of the device.

In your case I would have some small partition on the SATA drives to host the raided root and swop partitions, in addition to the flash drive.

All of RAID1, RAID10 and RAID5 can survive one disk malfunctioning. With 4 disks RAID1, 0+1, 1+0 and RAID10 can survive 2 disks failing in something like 66 % of the cases. A RAID6 would survive 100 % of 2 disks failing. Surviving here means continuing to run when the disks fail, and also ability to boot the system with the failed disks.

There is more on Linux RAID at [http://linux-raid.osdl.org](http://linux-raid.osdl.org)

---

