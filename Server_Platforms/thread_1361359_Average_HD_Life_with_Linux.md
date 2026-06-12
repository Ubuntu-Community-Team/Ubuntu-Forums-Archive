---
title: "Average HD Life with Linux"
date: 2009-12-21
forum: Server Platforms
---

### Post by Vegan on 2009-12-21
I was wondering if there is any study on how long disks last with Linux as opposed to Windows for servers?

I have seen some general material but I wanted to see if Linux was good at keeping a disk healthy.

My current boot disk has under 500 days of operational service at present so I expect it will last 3-5x longer at least.

I have the power options set to turn off the disk when the server is unused. I also have the CPU throttled back when unused as well.

Given a 1% workload, how much service life can I expect realistically?

---

### Post by falconindy on 2009-12-21
Too many variables to give an answer because there's too many things Linux can do to alter the behavior of a drive.

The way a drive is mounted can have an effect on the life of a drive (relatime v. noatime v. <unspecified>). The hdparm utility can be used to change physical attributes of the drive.

1% workload is a pretty ambiguous quantity. Even to give an absolute quantity of something like "this drive will operate for 4 hours per day" is up to interpretation. Will it be accessing the same spot on the disk for those 4 hours? Will it be constantly seeking, reading and writing small files? Both of these scenarios have different effects on the physical integrity of the drive.

Will the drive be power cycled every day? Will it be constantly spinning? This too, has an effect.

And then there's, of course, Murphy's Law. There's really no telling when a drive will die or how long it will last. I, personally, try not to keep drives for more than 3-4 years.

---

### Post by windependence on 2009-12-21
Spinning down and spinning up drives is extremely hard on them. Everyone thinks they are saving their drives when in actuality they are killing them. Good air circulation and spinning all the time is usually the best for drives - for that matter it's best to keep your equipment on 24/7.

-Tim

---

### Post by tgalati4 on 2009-12-21
Some google researchers wrote an interesting paper on hard disk failure modes.  You can google for it.  They go through a lot of disk drives so they have some sophisticated monitoring methods to evaluate drive health.

Bottom line, after 2 years, failure rate goes up measureably.  After 5 years, drives are considered aged out.  At home, I have a few drives that are 10 years old.  But they are not used that much and I power them up just to make sure they can still spin.

---

### Post by lukeiamyourfather on 2009-12-22
Agreed that there are too many variables to make any useful predictions about disk life. I'm sure environmental factors like temperature and vibration will play a much larger roll than what operating system is used.

---

### Post by lukeiamyourfather on 2009-12-22
> **tgalati4 said:**
> Some google researchers wrote an interesting paper on hard disk failure modes.  You can google for it.  They go through a lot of disk drives so they have some sophisticated monitoring methods to evaluate drive health.

Bottom line, after 2 years, failure rate goes up measureably.  After 5 years, drives are considered aged out.  At home, I have a few drives that are 10 years old.  But they are not used that much and I power them up just to make sure they can still spin.

Here's an article about it with links.

[http://storagemojo.com/2007/02/19/googles-disk-failure-experience/](http://storagemojo.com/2007/02/19/googles-disk-failure-experience/)

This is a good one too.

[http://storagemojo.com/2007/02/20/everything-you-know-about-disks-is-wrong/](http://storagemojo.com/2007/02/20/everything-you-know-about-disks-is-wrong/)

---

### Post by Vegan on 2009-12-22
I have heard Linux is hard on SSD disks, is there any hard facts for this as a boot disk?

---

### Post by lukeiamyourfather on 2009-12-22
> **Vegan said:**
> I have heard Linux is hard on SSD disks, is there any hard facts for this as a boot disk?

By hard I assume you mean it writes a lot of unnecessary stuff to the disk. In that respect I would guess its better than Windows because Linux doesn't use paging, so the disk won't be used until the system runs out of memory and needs swap. There are miscellaneous logs and such that get written to the disk but I'm sure those could be disabled too. Cheers!

---

### Post by falconindy on 2009-12-22
> **lukeiamyourfather said:**
> By hard I assume you mean it writes a lot of unnecessary stuff to the disk. In that respect I would guess its better than Windows because **Linux doesn't use paging**, so the disk won't be used until the system runs out of memory and needs swap. There are miscellaneous logs and such that get written to the disk but I'm sure those could be disabled too. Cheers!
You're misinformed. Linux absolutely uses paging in the same sense that Windows (and any other reasonable OS) does. Just because Microsoft calls it a pagefile and Linux calls it a swap partition (or swap file) doesn't make its usage any different.

---

### Post by hessiess on 2009-12-22
Just put the swap partition on a HDD, or don't have one at all, new systems usually have ample memory available.

---

### Post by lukeiamyourfather on 2009-12-22
> **falconindy said:**
> You're misinformed. Linux absolutely uses paging in the same sense that Windows (and any other reasonable OS) does. Just because Microsoft calls it a pagefile and Linux calls it a swap partition (or swap file) doesn't make its usage any different.

Are you sure about that? Note when starting up a Linux system the swap is 0 KB. Check the paging file size in Windows after starting up and you'll notice its hundreds of megabytes. Windows uses the paging file right away for storing some information even if there's physical memory available (some applications like Adobe products use the paging file extensively even if physical memory is available). Windows also uses the paging file for virtual memory when the physical memory is full but that's not the only thing its used for. Linux swap is not used until there's no more physical memory available and never before that.  Long story short, Windows paging and Linux swap are not the same thing. This is a noteworthy difference in the context of SSD since they have limited number of write cycles. Cheers!

---

### Post by Vegan on 2009-12-22
I have 1.5 GB so I am not short for a 32-bit platform. Even the old Pentium III had 768 MB so I do not really think the /swap is needed.

With Windows, you can get rid of the swap file but some programs are hard-coded to use it so you need to test the software stack to see if it works OK with no swap file.

---

### Post by falconindy on 2009-12-22
> **lukeiamyourfather said:**
> Are you sure about that? Note when starting up a Linux system the swap is 0 KB. Check the paging file size in Windows after starting up and you'll notice its hundreds of megabytes.
I'm positive.

Notice that after hours of usage, Windows' page file has likely not changed in size because its a reserved allocation of disk space. 
I say likely because initially, the page file was a static size. I believe in Win2k (may have been XP) MS implemented the ability to make it a dynamic size with a min and max value. In concept, it is identical to making a swap **file** in Linux. Because disk access is exceptionally slow compared to RAM access, a contiguous section of disk is the only proper way to utilize a page/swap file.

If Linux did not use paging, your computer would grind to a halt and eventually crash if and when you ran out of RAM.

---

### Post by lukeiamyourfather on 2009-12-22
> **falconindy said:**
> I'm positive.

Notice that after hours of usage, Windows' page file has likely not changed in size because its a reserved allocation of disk space. 
I say likely because initially, the page file was a static size. I believe in Win2k (may have been XP) MS implemented the ability to make it a dynamic size with a min and max value. In concept, it is identical to making a swap **file** in Linux. Because disk access is exceptionally slow compared to RAM access, a contiguous section of disk is the only proper way to utilize a page/swap file.

If Linux did not use paging, your computer would grind to a halt and eventually crash if and when you ran out of RAM.

We're kind of getting off topic, but I'm still not convinced. Why does the task manager show "PF Usage" on the performance tab, and its never at zero. Even five seconds after booting up when there's many GB of free memory there will be hundreds of megabytes shown as used in the paging file. Also looking at the memory usage and VM size in the processes, they are different values for most processes so even with memory available there's already paging file used.

---

### Post by falconindy on 2009-12-22
> **lukeiamyourfather said:**
> We're kind of getting off topic, but I'm still not convinced. Why does the task manager show "PF Usage" on the performance tab, and its never at zero. Even five seconds after booting up when there's many GB of free memory there will be hundreds of megabytes shown as used in the paging file. Also looking at the memory usage and VM size in the processes, they are different values for most processes so even with memory available there's already paging file used.
This has absolutely no bearing on how Linux operates, and is merely a difference between the two OS's and how they manage virtual memory. They use different means to accomplish the same ends.

If you want to get into the nitty gritty, paging and swapping are technically different, but not too dissimilar. Swapping involves unloading an entire process from RAM onto disk. Paging is moving pages (4k chunks) of less often used RAM to disk.

Want some supporting evidence to Linux using paging?

[http://en.wikipedia.org/wiki/Paging](http://en.wikipedia.org/wiki/Paging)
> Linux and other Unix-like operating systems use the term "swap" to describe both the act of moving memory pages between RAM and disk, and the region of a disk the pages are stored on.

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=89](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=89)
> One basic concept in the Linux implementation of virtual memory is the concept of a page. A page is a 4Kb area of memory and is the basic unit of memory with which both the kernel and the CPU deal. Although both can access individual bytes (or even bits), the amount of memory that is managed is usually in pages.

And hey, let's just grab a post from the lkml (linux kernel mailing list):
[http://lkml.org/lkml/2003/6/3/182](http://lkml.org/lkml/2003/6/3/182)

---

### Post by Raistlin355 on 2009-12-22
> **Vegan said:**
> I have heard Linux is hard on SSD disks, is there any hard facts for this as a boot disk?

I am curious, where did you hear this?  I ask cause I am going to build a new server soon and was thinking on getting an ssd boot drive.  Also the drive that I have in my current server is an old Seagate IDE 40Gb drive that I have been using non stop for 6 years.  That being said I also have my server and machines that stay on all the time in a separately cooled room in my house.

---

### Post by lukeiamyourfather on 2009-12-22
> **falconindy said:**
> ...merely a difference between the two OS's and how they manage virtual memory.

[QUOTE=lukeiamyourfather]Long story short, Windows paging and Linux swap are not the same thing.[/QUOTE]

Thanks for the links, but that's what I've been trying to explain to you all along. Swap and paging are not the same thing and you were saying they were. Glad we're on the same page now.

---

### Post by falconindy on 2009-12-22
> **lukeiamyourfather said:**
> Thanks for the links, but that's what I've been trying to explain to you all along. Swap and paging are not the same thing and you were saying they were. Glad we're on the same page now.
/headdesk

Sigh. I was referring to swap and page as the names that each OS gives to the general concept of moving memory from RAM to disk. Understand that Linux and Windows both use paging **and** swapping.

---

### Post by lukeiamyourfather on 2009-12-23
> **falconindy said:**
> /headdesk

Sigh. I was referring to swap and page as the names that each OS gives to the general concept of moving memory from RAM to disk. Understand that Linux and Windows both use paging **and** swapping.

The original poster asked if Linux was hard on SSD and I was pointing out how its probably easier on a SSD than Windows because it won't ever swap anything until its completely out of physical memory. Here it is in a nutshell, ready? **[COLOR="Red"]Windows will page things even when its not out of physical memory.[/COLOR]** This causes more write cycles on the SSD in everyday use making it "harder" in theory on the SSD than Linux would be. Nothing more, nothing less.

---

### Post by Vegan on 2009-12-23
I have researched SSD hardware and I have noticed a wide range of opinions as to how long they last. With growing logs such as my Apache2 logs which currently are rotated etc suggest a lot of writes in a single area will lead to the failure.

To that end some drives have firmware to deal with that by moving logs etc around so that no area is unduly stressed.

I am still waiting on a new disk for the Windows box as the current disk is almost 4 years old and I am concerned about its life expectancy.

---

### Post by jmore9 on 2009-12-23
I think all 10 of my hard drives are at least 6 years old for the youngest.  I run them until they grind to a stop.  Always backing up my data along the way of course.

I am still using a 12 year old western digital 20 giger which runs just fine a little noisier now then before but works just fine.

I had 3 maxtor 40 gigs which failed one right after the other back in 2002 i think it was.  Gave up one maxter and have always bought western digital since.

---

### Post by Vegan on 2009-12-23
My old 30GB Maxtor disk bit the dust last march after 5 years of service.

I have found disks do not last long in my shop as I use my computers aggressively for a lot of jobs.

Google seems to kill a lot of disks after only 5 years.

---

