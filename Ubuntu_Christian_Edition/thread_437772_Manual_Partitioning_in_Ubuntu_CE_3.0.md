---
title: "Manual Partitioning in Ubuntu CE 3.0"
date: 2007-05-09
forum: Ubuntu Christian Edition
---

### Post by jopv on 2007-05-09
I have a new Thinkpad Z60T.  I tried to install Ubuntu CE 3.0 using the standard partitioning option (1st Guided option for dual boot) but it didn't work.  It then offered me the manual option.  I would like to dual boot with Windows but it looks like I have to do it manually.

I'm a newbie to Linux and I don't know much about partitioning except forva little theory.  Is there any standard, easy Ubuntu guide on partitioning especially on how to allocate the right amount of space for the different partitions?

I need all the help I can get.

---

### Post by ntaylor0909 on 2007-05-09
I am not very experience myself, but I can tell you how I do it.  I create my windows partition with for example 50% of the hard drive and leave the other half unpartitioned. Then I use the manual option on the Ubuntu installer and take the remaining space and create 2 partitions. the first one is the root partition. As for the size of this partition, use all of the unpartitioned space minus the space you need for the swap partition.  The second partition is the swap partition. from what I understand this should be about twice as big as the amount of RAM you have in your system. so for example if you have 1 gig of RAM, make the swap file 2 gigs or bigger. I know that some people create 3 or 4 partitions for their Linux install using different file systems for each. Some of the reasons are a separate partition for your usr folder. It works great with 2 partitions, so I haven't found a good reason to switch.:KS

---

### Post by mysticrider92 on 2007-05-09
I would probably just cut the Windows partition in half using the Ubuntu partitioner (use the Windows disk defragger first). I personally don't use much of a swap partition (something like 256 megs on a system with 1 gig of ram, mostly to save hard drive space), but some might want larger. Then make a single ext3 partition for Ubuntu with the left over space to use as your / partition. There are more complex ways to do it (seprate /home, /usr, /var, etc), but they are not really necessary (a seprate /home partition is good for making backups, but otherwise not useful).

---

### Post by jopv on 2007-05-11
Thanks a lot for the information.  I believe there should standard Ubuntu step-by-step documentation on partitioning for newbies.  This is one of the key things when you transition to Linux.

---

