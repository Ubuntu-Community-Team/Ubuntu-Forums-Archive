---
title: "Freenas to Ubuntu Server worries"
date: 2011-08-28
forum: Server Platforms
---

### Post by johnsonld123 on 2011-08-28
I have been running Freenas for years and now want to move to Ubuntu server. Right now I have been playing with the idea of transforming Ubuntu desktop to server because of the newbness. Anyway I am currently running Ubuntu 11.04 and have my old freenas drives (1TB and 500gb) in a usb external EZ-Dock 2. I have tried numerous ways for weeks to mount the drives which I have had some success.
When I run sudo fdisk -l I get:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000aa32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24257   194836480   83  Linux
/dev/sda2           24257       24322      522241    5  Extended
/dev/sda5           24257       24322      522240   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce0f8af1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60564   488386583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121127   976762583+  ee  GPT

Some research over the weeks and have only been able to mount one drive with:

sudo mount -t ufs -o ro,ufstype=ufs /dev/sdg /media/movies

which was a small relief due to all the media I have on there
but if I try to mount my 500gb drive
both disappear and I have to reboot to get access.
I hate to post and I have utilized the search option but I just cannot find a permanent solution. I have raed  of the issues with large drives and GPT but if I can mount each drive separately I kind of think its a issue with the e-z dock.(which I was told could manage up to 2tb. I am 
reaching the option that I might have to keep things as is and wait until I have completed my server build and transfer files from the old drives to the new server and format for reuse.


EDIT: Nevermind 
I think I have found the answer or close in another thread

[http://ubuntuforums.org/showthread.php?t=1745259&highlight=freenas](http://ubuntuforums.org/showthread.php?t=1745259&highlight=freenas)

 			 			 			 		   		 		 		The backup only backs up the freenas configuration file, so you can move to another freenas  machine, reload the backup configuration file and you are up and  running with all of your defined shares, etc.  It works quite well.  As  far as data backup, you run some risks.  Freenas uses a different partitioning scheme and a different file system than Ubuntu.

Freenas is not really designed for  upgrading.  It's current, stable version is 7.2 and version 8 is a  complete rewrite with many features still not working.  So if you  installed 7.2 you will be good for many years.  If you are moving from freenas  (which is a an excellent NAS) to a full-fledged server (such as Ubuntu  server), there is no simple way (that I know of) to move the data  without having another 4 TB NAS to hold the data, build the new server,  then migrate the NAS-held data to the server.  Any other solution justs  puts your data at risk.

I think you are asking: "Can I overwrite freenas with Ubuntu server and keep my 3 TB of data?"

No.

When you built a freenas server, you are committed to that solution.

---

### Post by yaneurabeya on 2011-09-01
Why are you interested in converting FreeNAS over to Ubuntu server?

---

