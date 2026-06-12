---
title: "How to completely wipe out data from all disks ?"
date: 2015-11-22
forum: Server Platforms
---

### Post by soamz on 2015-11-22
I have a dell R510 server which has 5 SAS drives, 2TB each. 
I was using it for a caching server.
All 5 drives were configured as RAID0, I guess.
Now I want to use it for something else, so I need to install Debian to it. 

But how do I wipe out all the data from the whole 5 SAS drives ?

And I have attached one 120GB SSD to one of the caddy. 
I want to install the debian to the SSD only.

How do I tell the boot manager to install the OS to SSD and not to the RAID Controller drives ?

---

### Post by darkod on 2015-11-22
First, if they are really in raid0 they are not worth much. If any disk fails you lose all the data. So raid0 is not something useful on a server, and depending what you will use it for now. If you decide to create different level raid array, destroying the raid0 and creating a new raid1 or raid5 for example, will destroy all data anyway. Don't worry too much about it.

Second, you want to install on the 120GB anyway, so it doesn't matter if the raid array has data or not.

As for selecting the correct location, that's very easy on the partitioning step. I assume you will use manual partitioning (not one of the guided methods), because that gives you more flexibility and control. But even when using a guided method it will ask you which disk to use when you have more than one. For the manual setup, there will be a list of available disks, and the 120GB disk will be there.

Simply position the selection on it, and hit Enter. That will ask you if you want to write new partitioning table. Do that and all existing partitions and data will be deleted. Then you will see FREE SPACE created below the name of the disk. Select the free space and that is how you create partitions. When creating partitions make sure to select filesystem to use (Use As) and a mount point. Linux works with mount points, any partition is useless without one.

That's all you need to do. You can also find many tutorials with screenshots on the internet.

---

