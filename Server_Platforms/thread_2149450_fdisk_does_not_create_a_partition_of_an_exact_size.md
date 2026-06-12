---
title: "fdisk does not create a partition of an exact size for using it in Raid, sfdisk does"
date: 2013-05-28
forum: Server Platforms
---

### Post by PavelMan on 2013-05-28
Here is a puzzle: I have a raid6 drive array, assembled with mdadm, and one drive failed. These are four 2TB drives. I have done mdadm --fail /dev/md0 /dev/sdb1, replaced the drive, put another one in (had to shut down, no hot swapping available), rebooted and wanted to do fdisk to create a partition. But whenever I do that, an absolutely weird thing happens - it always creates a smaller partition than I need. 

Fdisk asks for the starting sector, then for the end one. I put the 2048 and 3900704767 respectively, as it is on all other drives, and do "w". But then, when checking through fdisl -l , I see "end" being 2xxxxxxxxx -something. Basically, it started to feel at some point, that the number I am trying to enter is too big. But I checked the "total" - it is 3907029168, which is greater than what I was trying to put in. 

This is what other drives have:

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
164 heads, 44 sectors/track, 541439 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5454118f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3900704767  1950351360   fd  Linux raid autodetect


But whenever I was doing it for sdb - it was showing 2-something in the "End" column. I have even tried to use "+" whatever is (3900704767 - 2048). Still the same result. But then I have stumbled upon sfdisk and have done  sudo sfdisk -d /dev/sdc | sudo sfdisk /dev/sdb, and it worked!

Why?? I am rebuilding the array now, but can not shake off this strange feeling that one day something may go wrong, and I will have to do it manually instead of cloning from another drive, and fdisk would not work...

Aside from that, I have received a warning, saying that the logical boundaries do not match the physical boundaries (of those sectors, I guess). So, theoretically, the performance of this "cloned" partition is "suboptimal". 

And I have been in this situation with 2tb drives before. Same problem. Sometimes you do not care much about data on the array, and can just rebuild the whole thing, but what if you do?

For a while, I thought that maybe I had to create smaller partitions on other drives to account for small variations in drive sizes. But first - I think I did. And second - why did sfdisk worked then, if it is just not possible to create a partition like that on this drive?

Any suggestions would be highly appreciated, as I have a feeling I am not alone, facing this issue.

---

### Post by darkod on 2013-05-29
I prefer parted to make partitions. You can change the unit size to sectors, MiB, GiB, basically it covers all options, and creates perfectly the partitions with the start/end values you enter.

It looks to me like fdisk is far from the perfect tool for partitioning. Apart from doing a quick fdik -l, I don't use it for anything else. Rather use cfdisk instead.

---

### Post by rubylaser on 2013-05-29
I use parted to make my original partitions, then I use sgdisk to make exact duplicates of the partitioning to my other array members.  You can duplicate the partitioning like this.
```

apt-get install parted gdisk

```

```

sgdisk --backup=table /dev/sdc
sgdisk --load-backup=table /dev/sdb

```

---

### Post by PavelMan on 2013-05-29
Thanks for the suggestion. I am not sure why I was always using fdisk. Ok, maybe I will even try those tools now - fail a disk, and try to re-partition it with either parted or cfdisk, and see how it goes. 

As far as alignment of physical and logical sectors goes - is it all taken care automatically by just selecting a "start" point as sector 2048? And then cloning of the partition - how safe is it to do across different drives? I have seen such a table once for sfdisk - it looked pretty innocent, just some basic info you choose during the configuration. Is it the same with sgdisk?

# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=     2048, size=3900702720, Id=fd

---

### Post by PavelMan on 2013-05-29
It worked absolutely beautiful, and I am resyncing the drive back into the array now, will be there in just 10 hours ;-). I have switched units to sectors with units s, and was able to indicate start and end as I needed them to be. Then set the flag to raid. I was doing it "interactively", as I did not know all commands I needed when I fired up parted, and was reading on it as I progressed.

I have started it with ```
sudo parted -a optimal /dev/sdb 
```, though, the meaning of which is still not completely clear to me, but I hope this partition is all very well aligned now to an underlying physical structure of the drive. Does anybody have a comment on this?

---

### Post by rubylaser on 2013-05-30
I cover partitioning in my [SnapRAID tutorial]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04").  The optimal setting will properly align the partition to your disk's geometry. And, it also has a method to test that it's aligned correctly.

---

