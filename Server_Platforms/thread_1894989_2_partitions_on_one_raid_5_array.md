---
title: "2 partitions on one raid 5 array?"
date: 2011-12-13
forum: Server Platforms
---

### Post by kochecc2 on 2011-12-13
I'm a bit lost. I have a home server running Ubuntu Server 10.10, and it has the whole file-system (/) on a 2gb flash drive (I know it's bad), with a 3-disk (2TB each) raid 5 as file storage only. 

I want to re-install Ubuntu Server and shrink the partition on my raid array so i can add another partition (still spanning all 3 drives) for the file-system, leaving the flash drive just for /boot. 

I have searched all over and have not been able to find a guide to do this, because this seems like something that does not get requested very often. 

Let it be known that I have already re-sized the main partition on my raid array from 4TB to 3.8TB using the partition-er on the Ubuntu Server 11.10 disk, but when I tried to have the installer create a new partition as / on the free space it just told me it failed to create it.

Thanks,
Chris

---

### Post by a2j on 2011-12-14
I think, what you need to do is LVM.

---

