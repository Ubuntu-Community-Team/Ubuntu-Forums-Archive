---
title: "Partition ends at Total Number of Cylinders + 1???"
date: 2011-07-28
forum: Server Platforms
---

### Post by CyberAngel on 2011-07-28
I made a fresh ubuntu server installation with two of the same hard disk drives in RAID1 mode.
When the installation finished, I had some errors in random times rendering the system unresponsible```
end_request: I/O error, dev sda, sector <Number>
```
From the above error, it looks like there was a problem with disk sda so I decided to change it with another same disk and rebuild the RAID1.

When I put the new hard disk on it, created a raid partition of the maximum allowed size and tried to add it to the raid array (after having removed the previous disk) I got an error saying that the new partition is not large enough to join this existing RAID1 array!
Then an "fdisk -l" command shown something weird...

The existing working hard disk in the RAID shows that it has 38913 cylinders but the partition starts at 1 and ends at 38913+1=38914!!
How is this possible? When I create a partition myself I am not allowed to put numbers larger than the total number of cylinders!

```
# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, [COLOR="Red"]38913[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcbc1cbc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       [COLOR="red"]38914[/COLOR]   312569856   fd  Linux raid autodetect
```

---

### Post by oldfred on 2011-07-28
Hard drives have not used cylinders since drives went over 8GB. You really need to look at it by sectors as cylinders get rounded. And often rounded up.

```
sudo fdisk -lu
```

I do not know RAID, but there was another post a month or so ago where a user had a different drive and he could not set the size as large as his other drive. I think the only solution was making the other drive slightly smaller.

---

### Post by CyberAngel on 2011-07-28
Thank you very much for the reply oldfred!

Your post saved me :)
When I used "fdisk -u /dev/sda", I could setup the partitions using sectors as start/end numbers and I made the partition exactly the same number of sectors with the existing one! Now the RAID rebuilds fine!

---

