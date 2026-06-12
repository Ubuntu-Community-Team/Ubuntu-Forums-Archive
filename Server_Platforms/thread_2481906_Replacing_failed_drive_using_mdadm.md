---
title: "Replacing failed drive using mdadm"
date: 2022-12-12
forum: Server Platforms
---

### Post by richardcaney on 2022-12-12
I have a test server running Ubuntu Server 22.04.

The server boots from a small SSD. When setting it up I used mdadm to create a RAID1 with two 1 TB drives for data. After a few months, one of the drives failed. The mirror works. I was able to continue using the server while waiting for a new repalcement drive to arrive.

I followed some instructions in a video I found online and was able to replace the drive and rebuild the array.

One thing bothers me when viewing things using lsblk:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291411&stc=1[/IMG]

The original, still-working RAID member is sde. The new replacement is sdd. I followed the instructions in the replacement video in creating the partition sdd1. No such partition is showing for sde.

Running mdadm --detail /dev/md0 shows no errors:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291412&stc=1[/IMG]


Did I miss a step creating the original RAID1 array? Should I take some corrective measures or leave well enough alone?

---

### Post by slickymaster on 2022-12-13
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2022-12-13
> **richardcaney said:**
>  Did I miss a step creating the original RAID1 array? Should I take some corrective measures or leave well enough alone?

Yes, you did.  Some people think that having partitions when the whole drive will be used in an array isn't necessary. Obviously, they are correct, but when it comes time to replace a failed drive, partitions provide options that don't exist otherwise.

Should you correct it?  Up to you.  As much as I like to have a perfect setup, I'm also lazy.  When the non-partitioned drive fails, that's when I'd fix it ... or when it is time to use larger HDDs and a mass migration happens.

BTW, you didn't setup the new drive correctly either.  You created a partition, but ignored it when you added it to the array.  That's shown clearly in the lsblk output AND in the mdadm --detail output.

BTW, please, please, please don't post images of text.  Copy/paste the text and use forum 'code-tags' so everything lines up.  Here's a few RAID1 arrays here, with the lsblk output clearly showing what I mean:
```
NAME      SIZE TYPE  FSTYPE            MOUNTPOINT
sdb       1.8T disk                    
&#9500;&#9472;sdb1    128M part                    
&#9500;&#9472;sdb2    9.8G part  ext4              
&#9500;&#9472;sdb3    1.8T part  linux_raid_member 
&#9474; &#9492;&#9472;md1   1.8T raid1 ext4              /raid
&#9492;&#9472;sdb4      1M part  ext2              
sdc       1.8T disk                    
&#9500;&#9472;sdc1    9.9G part  ext4              
&#9492;&#9472;sdc2    1.8T part  linux_raid_member 
  &#9492;&#9472;md1   1.8T raid1 ext4              /raid
sdd       1.8T disk                    
&#9500;&#9472;sdd1  125.5M part                    
&#9500;&#9472;sdd2    1.3T part  linux_raid_member 
&#9474; &#9492;&#9472;md2   1.3T raid1 ext4              /Data/r2
&#9492;&#9472;sdd3    586G part  ext4              
sde       1.8T disk                    
&#9500;&#9472;sde1  125.5M part                    
&#9500;&#9472;sde2    1.3T part  linux_raid_member 
&#9474; &#9492;&#9472;md2   1.3T raid1 ext4              /Data/r2
&#9492;&#9472;sde3    586G part  ext4              

```

---

### Post by richardcaney on 2022-12-13
"You created a partition, but ignored it when you added it to the array."

Yes, everything was going smoothly until I tried to add "sdd1" (the partition I had just created). I got an error message stating that the drive size was not a match. I was only able to add the new drive as "sdd".

Thanks for your explanation. I have backups so I'm inclined to go back and do it right.

---

### Post by TheFu on 2022-12-14
One of the key reasons for using partitions is the ability to set the exact size to be consistent across different sized and different vendor's drives. If you redo them, set the partition sizes to something exact.

Keep the exact commands as part of the run-book for the system.  Same applies to the array creation commands. Really, any important system changes or setups should be part of the run-book for a system.  Networking, disk layouts, RAM sizing, and any non-standard (for me) infrastructure stuff all go into the run-book.  It can be paper, a text file, or a wiki.  Just be certain that if the building is gone, you don't lose it.   I use vimwiki text files.  Because the run-book can hold sensitive information, I place it in /root/ in the same place where daily key system information is captured prior to running backups.  Sometimes, it is easier to have some specific information, to aid recovery to completely new hardware.  All that stuff, along with the run-book, go into 1 place.  I always backup /root/.  Always.

---

### Post by richardcaney on 2022-12-14
Excellent advice! I'll follow your tips, especially the "run-book".

---

