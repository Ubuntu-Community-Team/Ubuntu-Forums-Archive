---
title: "My Experience"
date: 2008-05-04
forum: Testimonials &amp; Experiences
---

### Post by Phenax on 2008-05-04
For years now I've been using more or less "roll-your-own distributions." It was just taking too long to maintain in some aspects and right now my life is not leasing my time easily.

I figured I'd install Ubuntu 8.04 and see how well it fairs. I installed it both on my Desktop, and my friend's laptop (He was a bit of a newbie, and I had previously thrown Arch on there, but I thought Xubuntu would be a better choice).


**Installation:**
Most everything went well, but the partitioner could be improved to handle more situations.

On my desktop, I wanted to preserve a partition or two, so I went in manually. I was resizing my / partition, and it threw me an error and left 8mb of free space between two partitions. I could not get the partitioning tool to expand this space. I eventually resized it in the partition table, converted it to ext2, used resize2fs, and converted it back to ext3.

On my friend's laptop, it kept saying there was an error making the file-system. I then noticed that /dev/sda[1-9] wasn't even there. I fdisk'd it, and the partitions were there, as well as in the partitioning tool. I had to reboot for /dev/sda[1-9] to be made in the filesystem.


**Running (so far)**
The last time I tried Ubuntu, I jumped through loopholes getting proprietary drivers to work. I was pleasantly surprised by it suggesting to install Nvidia drivers. On the laptop, it installed Atheros drivers for wireless quick and painlessly.

I was also surprised by little things: Firefox could install plug-ins via the package manager easily.

On the laptop, I had to do some configuration-file hacking to get sound to work.. There has been a bug filed for quite some time about the issue, but ultimately I believe it boils down to upstream ALSA fixes.


**Overall:**
I think I'll be sticking with Ubuntu. It's very nice and relatively user-friendly.

My only concern is some of the problems I encountered would probably have been show-stoppers for newbies; hopefully newer releases can concrete Ubuntu.

---

### Post by chewearn on 2008-05-05
Partitioning a harddisk will always be a major stumbling block for installing a second OS (dual boot situation).  You need the software to becomes so smart, it can take care of all hardware and software combination.

Of course, rather than build an AI-based partitioner, the easiest solution is if you simply force "Install on the entire harddisk" option, and wipe out other silly competing OS.  :lol:

Wait, before I got blasted, the other OS (shall remain nameless) is doing this all along.  :lol:

---

