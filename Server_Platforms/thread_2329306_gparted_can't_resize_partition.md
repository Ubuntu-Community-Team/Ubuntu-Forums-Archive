---
title: "gparted can't resize partition"
date: 2016-06-29
forum: Server Platforms
---

### Post by HankB on 2016-06-29
Hi folks,
Situation: I'm replacing the hard drives in my backup server with larger drives (2TB -> 3TB) The drives have one small boot/root partition and one large data partition. Both partitions are RAID1 between the two drives. (At present it is only one drive operating a degraded RAID1 since the other drive failed.)

Steps I have taken:
 - bitwise copy of the remaining good 2TB drive to a 3TB drive. (using dd)
 - Run gparted to fix the partition table This leaves about 1/3 of the drive unallocated.
 - try to use gparted to resize the data partition.

Here's where things go sideways. The only option available when I select the partition I want to resize is to delete it. Option to resize is grayed out. Things I checked/tried
 - no partition on the drive is mounted.
 - The RAID is not active (/proc/mdstat shows nothing.)
 - I tried unsetting the RAID flag and restarting gparted. No change
 - reset the RAID flag and tried again.

None of these made any difference.

Is there any hope to resize the RAID partition? I'd really prefer to do that rather than have to stat from scratch with this drive.

Thanks!

---

### Post by oldfred on 2016-06-30
I do not know RAID.

But your 3TB drive must be gpt(GUID) partitioned. 
Your 2TB drive could have been either MBR(msdos) or gpt. 
If 2TB was MBR, then your dd converts your 3TB drive to 2TB and it cannot be increased as 2TB is the max for MBR. 

You need to convert to gpt.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]http://en.wikipedia.org/wiki/GUID_Partition_Table

[/URL]
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT) 

Have no idea if this works with RAID or not:

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]
[/URL]

---

### Post by HankB on 2016-06-30
Hi oldfred,
Good point and something I forgot to check. I did just check and the partition table is already GPT. I've been using GPT partitions for a few years now and even though MBR could have worked for the 2TB drives I went with GPT when I first set them up.

I'm pretty sure that RAID is the issue. I've had difficulty repartitioning drives that had formerly been in a RAID until I zeroed out the RAID signature. Obviously I cannot do that in this case. I suppose there's a good reason for gparted to not muck with RAID partitions. I think I'll have to bite the bullet and delete/recreate the partition and copy the data again. At least I don't have to mess with the boot/root partition and I'm comfortable copying the data partition while mounted as it will not be active at the time. (And in less time than it took to type this, it's done.)

Thanks!

---

### Post by darkod on 2016-07-03
Cloning the smaller disk is not the correct way to expand RAID storage. I assume you are talking about mdadm software raid, right?

You had only one 2TB disk in the raid1, in degraded mode, right?

You create the two partitions you need on the new 3TB disk. The smaller partition I assume will be the same size as the existing on the 2TB disk, you don't want to extend it. The bigger partition will be the rest of the 3TB disk.

After that you add those partitions to the respective mdadm arrays. The array size will remain the same because the smaller disk (partitions) is limiting the array sizes.

After the sync is done and you have a full array (not degraded), you remove the partitions of the 2TB disk from the arrays, you power off, replace the disk with a 3TB new disk, and create identical partitions as the 3TB disk already installed.

Then you add those partitions to the arrays and wait for sync. After that you tell mdadm to use the full max size for the big array (assuming the small array stays the same).

After that you're done... Needless to mention this, have a good backup of all data before trying all this, although the operation should rarely give you problems. But just in case...

---

