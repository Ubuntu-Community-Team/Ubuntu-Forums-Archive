---
title: "Running ubuntu server from USB pendrive"
date: 2009-03-20
forum: Server Platforms
---

### Post by mbrxjepp on 2009-03-20
I want to build a server based on one of these:

[http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVERS.html]("http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVERS.html")

and I'd like to run ubuntu server as the OS. I'm going to have 4 HDDs in a raid10 configuration (using a PCI controller) and I have read that it's possible to run the OS from two USB pendrives in RAID1 to guard against drive failure.

Unfortunately, I've no idea how to go about doing this and wondered if anyone has done anything similar?

Cheers, 

Ewan

---

### Post by Wayne_V on 2009-03-20
I've installed to one pen drive before -- nothing to it, just plug it in, boot the CD and install as normal.   Adding RAID to a second pen drive should be straightforward.

---

### Post by mbrxjepp on 2009-03-20
Sounds positive. Can you offer any more details? I'm a total novice...

Having looked through a number of install guides for ubuntu server, I'm not sure how I would direct the install to the pendrive rather than the RAID10 array.

Once installed, how would I go about setting up a second pen drive in RAID1?

Cheers!

---

### Post by Wayne_V on 2009-03-20
As long as your BIOS is configured to recognize the pen drives as bootable disks they should be presented as possible install disks during the install.  I believe the partioner portion of the installer will let you configure the install disk as  raid/lvm as well (it's been a while since I've  done an scratch install tho).

---

### Post by netztier on 2009-03-20
> **mbrxjepp said:**
> 

and I'd like to run ubuntu server as the OS. I'm going to have 4 HDDs in a raid10 configuration (using a PCI controller) and I have read that it's possible to run the OS from two USB pendrives in RAID1 to guard against drive failure.


Just a story in that context:

I'm running Ubuntu Server off a 4GB IDE flash module and use software RAID-1 with a pair of 500GB SATA-II disks. The Transcend IDE flash module has terrible write speeds. Therefore, I wanted to avoid writing to that disk too often, which should even do some good to the lifetime of the flash module anyway.

I run LVM2; my software RAID-1 /dev/md0 is (so far) the only PhysicalVolume for my VolumeGroup (mainVG), which I sliced up into LogicalVolumes like this:

```
user@server:~$ **sudo lvscan**
  ACTIVE            '/dev/mainVG/swapLV' [5.00 GB] inherit
  ACTIVE            '/dev/mainVG/varLV'  [50.00 GB] inherit
  ACTIVE            '/dev/mainVG/homeLV' [100.00 GB] inherit
  ACTIVE            '/dev/mainVG/dataLV' [250.00 GB] inherit
  ACTIVE            '/dev/mainVG/tmpLV'  [10.00 GB] inherit

```

which get mounted like this (not my actual **/etc/fstab**, just for illustration):

```

/dev/sda1                  /		    ext3    noatime,errors=remount-ro
/dev/mapper/mainVG-dataLV  /data           ext3    relatime        
/dev/mapper/mainVG-homeLV  /home           ext3    relatime        
/dev/mapper/mainVG-varLV   /var            ext3    relatime        
/dev/mapper/mainVG-swapLV   none           swap    sw              
/dev/mapper/mainVG-tmpLV   /tmp            ext3    relatime 
```	

Like this, no file system that's subject to a lot of writes resides on /dev/sda, which is my flash disk.

Note that I did create an LV for swap, an that swap is also on the mirror. Some guides suggest to exclude the swap partition from mirroring and to run two independent swap partitions instead. Well - losing half of your swap space when a disk fails probably will crash the machine pretty hard.

I had almost forgotten about /tmp, and when I started experimenting with certain programs, the server's performance came down to a crawl. Took my a while to find out why ;-)

Some software (Twonkymedia Server 5.0) also has the inconvenient habit of writing to some hidden directory in the user's home. So if you run it from a root shell, it starts to write to /root/.hiddendirectory instead of /home/root/.hiddendirectory, and all writes go to /dev/sda1 again :-( (ditched Twonkymedia, now using Mediatomb).

So if you're running server off flash or USB, take a close look at where your disk writes actually go, and make sure you know about them for all the server programs you intend to run. 

Consider running LVM2, so you have the possibility to adapt your partitioning scheme to changing needs. I also makes adding another set of disks a breeze, without having to reformat/rebuild the whole array. 

If you do, I would suggest to use only the RAID-1 function of your PCI controller. With your four disks, generate two pairs, and let the controller show the pairs to the OS as each a virtual disk. Then add both these virtual disks to LVM as PhysicalVolumes. LVM can then do the job of striping across these PVs. If you add more disks, let the controller pair them up and add the third virtual disk as a PV to LVM, and then grow and resize your LVs (and the file systems within) to suit your needs.

regards

Marc

---

### Post by mbrxjepp on 2009-03-22
Extremely helpful - thanks everyone. I think I need to buy all the hardware and start installing everything before I ask anything else, but at least I know it's possible!

Cheers, 

Ewan

---

