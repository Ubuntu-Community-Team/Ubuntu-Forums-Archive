---
title: "FAT in linux"
date: 2007-03-24
forum: The Cafe
---

### Post by jgrabham on 2007-03-24
When you format HDDs inlinux, why cant it just use FAT, would be much easier when using dual boots.

---

### Post by qpieus on 2007-03-24
Sure you can do that. Format as FAT32 any partition that will be shared between linux and windows. You can't install the linux filesytem on the fat32 partitions though. You can also install , in windows, a driver that will read a linux ext3 filesystem, so you wouldn't need any fat32 partitions in that case....

---

### Post by mykalreborn on 2007-03-24
> You can also install , in windows, a driver that will read a linux ext3 filesystem, so you wouldn't need any fat32 partitions in that case....
and [here]("http://www.fs-driver.org/") it is. 
linux uses ext3 because it's better than fat32. one of the key aspects is that you don't have to defragment it. that's just one of them, but i'm sure there are more.

---

### Post by saulgoode on 2007-03-24
FAT does not support owner, group, and world permissions to access files or directories (you have to either provide everyone access or no one). It also does not fully support case sensitivity in filenames and directory names (try to name a directory "FAT" in FAT :) ). FAT's date stamping is also rather arcane and frought with problems.

So, basically, FAT is not very capable for Linux *system* partitions and it is best if you just provide a separate FAT partition (if needed) for sharing files between the two OSes.

---

### Post by karellen on 2007-03-24
The FAT filesystem does not contain mechanisms which prevent newly written files from becoming scattered across the partition. Other filesystems, like HPFS, use free space bitmaps which indicating used and available clusters, which could then be quickly looked up in order to find free contiguous areas (improved in exFAT). Another solution is the linkage of all free clusters into one or more lists (as is done in Unix filesystems). Instead, the FAT has to be scanned like an array in order to find free clusters, which can lead to performance penalties with today's large hard disks and consequently their large FAT sizes. In fact, computing free disk space on FAT is one of the most expensive operations, as it requires reading the entire FAT linearly. A justification Microsoft offered for limiting the maximum size of FAT32 partitions created on Windows was the time required to perform a simple "DIR" operation, which always displays the free disk space as the last line. Displaying this line took longer and longer as the number of clusters increased.

well...that's FAT....it's obsolete and unreliable.

---

### Post by Engnome on 2007-03-24
Doesn't have a journal either, bigger risk of data corruption.

Doesn't support >4gb files.

---

### Post by enopepsoo on 2007-03-24
Doesn't FAT32 max out at some small number of gigs?  I think it is around 120 - 130 gigs.

I think there is a way to install Ubuntu onto NTFS, and if I am not mistaken, and I think that dyne:bolic will install to FAT.

---

### Post by DoctorMO on 2007-03-24
FAT32 maxes out at 4GB, that is why it's called FAT32 it's got 32bits of addressing space. like 32bit processors can only address 4GB of RAM without paging (swapping ram in and out)

when you say FAT I first think of FAT12, there was also a FAT16 too horrible, horrible formats used of floppy disks and early dos machines.

For sharing information with XP install the ruddy ext2 support for windows. I can't remember but it's either Microsoft extra package for unix compatibility or some other thing you install.

---

### Post by macogw on 2007-03-24
> **DoctorMO said:**
> FAT32 maxes out at 4GB, that is why it's called FAT32 it's got 32bits of addressing space. like 32bit processors can only address 4GB of RAM without paging (swapping ram in and out)

when you say FAT I first think of FAT12, there was also a FAT16 too horrible, horrible formats used of floppy disks and early dos machines.

For sharing information with XP install the ruddy ext2 support for windows. I can't remember but it's either Microsoft extra package for unix compatibility or some other thing you install.

That's maximum single-file size.  The above poster was referring to the fact that you can't format a 500GB hard drive in FAT32.  It has a maximum hard drive or partition size.

---

### Post by SavantEdge on 2007-03-24
Max size for a FAT32 partition is 32 GB, I believe.

---

### Post by cowlip on 2007-03-24
> You cannot format a volume larger than 32 gigabytes (GB) in size using the FAT32 file system during the Windows XP installation process. Windows XP can mount and support FAT32 volumes larger than 32 GB (subject to the other limits), but you cannot create a FAT32 volume larger than 32 GB by using the Format tool during Setup. If you need to format a volume that is larger than 32 GB, use the NTFS file system to format it. Another option is to start from a Microsoft Windows 98 or Microsoft Windows Millennium Edition (Me) Startup disk and use the Format tool included on the disk.

[Limitations of the FAT32 File System]("http://support.microsoft.com/default.aspx?scid=KB;EN-US;Q314463&")

FAT can go up to 4TB...although I'm sure only a masochist would use it in that case.  Of course there's also the max 4gb file limit that macgow mentioned.

---

