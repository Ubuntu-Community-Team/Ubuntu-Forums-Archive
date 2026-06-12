---
title: "Server installation on hardware RAID 0"
date: 2008-06-19
forum: Server Platforms
---

### Post by magicplayr2000 on 2008-06-19
Hi, I've seen a couple posts around here saying that you can't install ubuntu onto a RAID 0 array because it can't boot.  Is there a way to get around this problem?  I've got 2 500gb hard drives.

---

### Post by NateMan on 2008-06-19
What sort of hardware raid are you using? If its on motherboard hardware raid, it probably isn't true hardware raid, but in fact a fake raid setup which will not work very well. Also a server running raid0 is a huge risk. If one of your two 500gig drives dies, which happens more than you might think, you will loose all of your data and it will be unrecoverable. In addition to that, if your using fake raid or software raid, you will see very little performance difference. A better idea might just be to not worry about raid and just use two harddrives. Either that or add a third drive and use raid5 if you have a hardware controller. Give us some info on your setup other than the two 500gig drives.

---

### Post by magicplayr2000 on 2008-06-19
It's an on-motherboard raid controller.  I'm going to be using this mostly as a file server.  If I don't raid them together, what would be a good way to distribute the data?  One drive would be a master drive, the other would basically be tucked away in /media/sdb and if I fill up the main hard drive, then I'd have to make sure no one else wrote to it and wrote to the second hard drive instead.  Or maybe I'm misunderstanding the situation.

Is there a way around this problem that doesn't involve raiding them?

---

### Post by olivero on 2008-06-19
Well, you cannot boot a raid 0 because it will shatter your data over two discs, making it useless for the boot loader, who just won't understand raids.

First advice: split your two drives into three partitions each:

1. 10GB
2. 2 GB
3. 488 GB

Build a md raid 1 on partitions 1 an 2 of both drives. Use the 10 GB partition for / and the 2 GB for swap. This way your system becomes more resilient and could reboot if one of the drives crashes.

With the 3rd partition you have to decide: throughput or safety?

Throughput: md Raid 0. If one drive of the two fails, all of your data is gone forever. But using **two** distinct channels of your motherboard IO, you almost double throughput to disk. (Actually it also depends on your block size and disc usage scenario, but you've got the chance disc IO will be fast). 488 GB * 2 = 996 GB capacity.

Safety: md Raid 1. Half the capacity = 488 GB, twice the security. If one drive fails, data is still there. Throughput is just about the same, compared to a single drive. Linux is really good at avoiding md raid 1 overhead.

For a file-server I suggest a third disc and a 3 disc raid 5. This would give you the 996 GB disc storage and the security that one disc can fail without impact on your data integrity. If you partition the third drive like the first two, you can add the 10/2GB partitions as spares to the root and swap raids, adding further resilience.

Oliver

---

### Post by NateMan on 2008-06-19
Normally you can't make a raid out of disk partitions. In software raid its impossible, although with your motherboard's onboard fakeraid. Personally I would strongly consider getting a third 500gig and making a software raid setup. That way if your mobo dies, you won't need an identical board to regain your data. Also the fakeraid doesn't give any extra performance, it actually uses more overhead. Software raid 5 is the same way, but it would be much easier from a data recovery standpoint. Then from there you can partition it as you see fit for os and data storage. Are you using ide or sata drives? If its ide, I would recommend buying an inexpensive hardware raid controller.

---

### Post by olivero on 2008-06-19
NateMan: Sorry to be unclear. I apologize. I said **md** raid meaning software raid. The onboard hw raid controllers will **not** work on partitions. Any onboard hw raid would appear as one large disc to linux, if the boot loader supports it.

---

### Post by KCPokes on 2008-11-04
> **magicplayr2000 said:**
> It's an on-motherboard raid controller.  I'm going to be using this mostly as a file server.  If I don't raid them together, what would be a good way to distribute the data?  One drive would be a master drive, the other would basically be tucked away in /media/sdb and if I fill up the main hard drive, then I'd have to make sure no one else wrote to it and wrote to the second hard drive instead.  Or maybe I'm misunderstanding the situation.

Is there a way around this problem that doesn't involve raiding them?

Just a thought, but why not just consider setting up the two drives via LVM, which will allow you to span across the two drives as they were one.  Thus you can have your root partition on one drive, combining the remaining space with the secondary drive to create your storage partition.  Data on the storage partition would not impact your root partition, plus you'd now have all additional space available as you'd like.

Obviously this is not fault tolerant, as a RAID 1 or RAID 5 setup would provide (granted you'd need at least 3 drives for RAID 5), but if you are just wanting to utilize the space from both drives, without failover, this might be an easier solution.

---

