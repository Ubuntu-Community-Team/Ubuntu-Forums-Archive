---
title: "In idiot, can someone explain what swap does?"
date: 2010-03-29
forum: The Cafe
---

### Post by themarker0 on 2010-03-29
As basic as you can. I left about a gig for mine. Is that enough?

---

### Post by _h_ on 2010-03-29
It's what your system uses when it runs out of available RAM, it starts using swap space to act like RAM.

1GB swap space is good if you don't mind the space loss and have low amount of RAM. People with higher amounts of RAM will want like 256mb-500mb of swap space as reserve since most of them don't use all their available.

It's basically like the Windows paging file, for Linux.

---

### Post by lisati on 2010-03-29
A swap partition is associated with memory management, and can help ease the pressure on your system when you're doing things which require a lot of memory. 

(I'm talking RAM here, not disk space)

---

### Post by doas777 on 2010-03-29
swap is a way to pretend you have more ram than you do. 
when your ram is getting full, the system will take chuncks of the data in ram, and save it to the harddisk, but still arranged like it was in ram(ram stores "pages" of data). 

that way it can clear room for somthing else. whenever it needs data that has been swapped to the hard disk, it just clears out enough ram for the info (probably by putting differant data to the disk), it retrieves the info off the disk and places it back in ram.

---

### Post by Cam42 on 2010-03-29
Yeah, as a general rule, Memory is RAM, and storage is disk space.

---

### Post by themarker0 on 2010-03-29
Ah thank you. So having a gig would be fine then (250 drive, i'll never use it all :P)

---

### Post by tica vun on 2010-03-29
If you have sufficient ram (2GB should suffice for normal desktop usage), you probably don't even need swap unless you hibernate your computer.

---

### Post by _h_ on 2010-03-29
> **themarker0 said:**
> Ah thank you. So having a gig would be fine then (250 drive, i'll never use it all :P)

Drive space has nothing to do with it. Swap space is used when your physical RAM is depleted, and your system starts using swap to act as RAM.

---

### Post by themarker0 on 2010-03-29
> **tica vun said:**
> If you have sufficient ram (2GB should suffice for normal desktop usage), you probably don't even need swap unless you hibernate your computer.

I only have 1.5gb.

---

### Post by swoll1980 on 2010-03-29
You should have 2x more swap space than RAM. If you have 512 MB RAM then 1GB swap is fine. 1GB RAM 2GB swap, and so on.

---

### Post by swoll1980 on 2010-03-29
> **themarker0 said:**
> I only have 1.5gb.

3GB swap is what you want.

---

### Post by MaxIBoy on 2010-03-29
If you ever plan to hibernate (not the same as suspend, with hibernate you can cut off power as well,) then you need at least twice as much swap as RAM. But if you don't need that capability, then you don't actually need that much and a gig of swap is fine. And keep in mind that restoring from hibernate is actually slower than a normal boot, so hibernate isn't really needed. I'd say a gig of swap is probably good enough.

---

### Post by ikt on 2010-03-29
> **swoll1980 said:**
> You should have 2x more swap space than RAM. If you have 512 MB RAM then 1GB swap is fine. 1GB RAM 2GB swap, and so on.

I believe this general rule becomes outdated once you reach 2gb of ram.

I have 4gb of ram and see no need for 8gb of swap.

---

### Post by Sef on 2010-03-29
> You should have  2x more swap space than RAM. If you have 512 MB RAM then 1GB swap is  fine. 1GB RAM 2GB swap, and so on.

That is not true today.   Normally, unless one wants to put it in as a safety measure, or wants to hibernate, then swap is not needed.  Certain exceptions apply for graphic intensive applications.  

As a safety measure, I would recommend, I gb swap, but for most people it is more of a security blanket than need.

For hibernation, you swap should be the same size as the amount of ram you have.

Read the [swapfaq]("https://help.ubuntu.com/community/SwapFaq").

---

### Post by swoll1980 on 2010-03-29
> **Sef said:**
> That is not true today.   Normally, unless one wants to put it in as a safety measure, or wants to hibernate, then swap is not needed.  Certain exceptions apply for graphic intensive applications.  

As a safety measure, I would recommend, I gb swap, but for most people it is more of a security blanket than need.

For hibernation, you swap should be the same size as the amount of ram you have.

Read the [swapfaq]("https://help.ubuntu.com/community/SwapFaq").

As a rule of thumb 2x swap is the safest bet. We all know it is better to have something, and not need it, than to need something and not have it.

---

### Post by koenn on 2010-03-29
> **Sef said:**
> That is not true today.   Normally, unless one wants to put it in as a safety measure, or wants to hibernate, then swap is not needed.  Certain exceptions apply for graphic intensive applications.  

As a safety measure, I would recommend, I gb swap, but for most people it is more of a security blanket than need.

For hibernation, you swap should be the same size as the amount of ram you have.


+1

the swap=RAMx2 rule is from way back, when you could still actually run out of RAM by running just a few programs. 

Also, swap is on disk. It's slow. If you think of the seek and read times associated with disk access, you really don't want to have that much swap - it's not really useful.  

At most, you need *some* swap to keep your PC from hanging when the RAM is all used up, so that it remains responsive while you kill a couple of processes.

---

### Post by koenn on 2010-03-29
> **swoll1980 said:**
> As a rule of thumb 2x swap is the safest bet. We all know it is better to have something, and not need it, than to need something and not have it.

8GB of swap just because you have 4 GB of RAM, is a waste of disk space.

---

### Post by doas777 on 2010-03-29
i've always been told 1.5x ram for swap, is needed for hibernation and whatnot. the actual formula would be:
```

x >= used-ram + currently-paged-ram

```
so 1x is not sufficient if any paging is already being done and ram is nearly full. 2x is just being extra safe.

I may not need it, but i am much more likely to accidentally click Hibernate, than I am to actually need that 2-5GB disk space these days.

---

### Post by swoll1980 on 2010-03-29
> **koenn said:**
> 8GB of swap just because you have 4 GB of RAM, is a waste of disk space.

I'm not trying to be disagreeable, but if you get to the point where 8GB of space will make or break you, then your going to have to buy a new drive anyways. I can't see some one with 4GB of RAM having storage issues anyways. Usually people with 4GB RAM have huge hard drives to go with it. I have 4GB RAM and 1.5TB storage.

---

### Post by koenn on 2010-03-29
not trying to be disagreable either, but 8 GB is 10 CD images, or hundreds of pictures, or an awful lot of documents. If I'm busy with something and I need that space and it isn't there, right now, unused swap is a waste of space, whether or not I was planning to get extra disks in a few weeks. 

Except for the obvious examples (hibernation, servers/hypervisors that need to stay up no matter what), by the time you're actually *using* 1GB of swap, you'll computer be so slow you'll think it's crashing, and you'll reboot it to fix the issue. The additional 5 or 6 or 7 GB of swap never get used.

---

### Post by Warpnow on 2010-03-29
People with big hard drives run  out of space, too. My 750gb hard drive had 0 bytes left free yesterday. Causes alot of odd errors. I had to start deleting things. Oddly, thunar wouldn't trash the files because it couldn't copy them or something. Had to drop into a terminal and use rm.

---

### Post by lisati on 2010-03-29
> **koenn said:**
> 8GB of swap just because you have 4 GB of RAM, is a waste of disk space.

:) Random musing: On my old desktop, which I sometimes power up as a backup for my server, an 8Gb swap partition would be, well, impossible as well as unnecessary. It has 64Mb RAM and a 3Gb hard drive. The machine is showing its age, but still works well enough for occasional use.

---

### Post by mkendall on 2010-03-29
> **themarker0 said:**
> As basic as you can. I left about a gig for mine. Is that enough?

Swap is the sticky note for when your computer is doing more at once than it can remember.

---

### Post by ikt on 2010-03-30
> **swoll1980 said:**
> I'm not trying to be disagreeable, but if you get to the point where 8GB of space will make or break you, then your going to have to buy a new drive anyways. I can't see some one with 4GB of RAM having storage issues anyways. Usually people with 4GB RAM have huge hard drives to go with it. I have 4GB RAM and 1.5TB storage.

[http://benchmarkreviews.com/index.php?option=com_content&task=view&id=328&Itemid=60](http://benchmarkreviews.com/index.php?option=com_content&task=view&id=328&Itemid=60)

;)

---

### Post by pbpersson on 2010-03-30
Is there a high water mark in Ubuntu?  In other words, where do you look to see the highest amount of swap you have ever used since the OS was first installed?

---

### Post by koenn on 2010-03-30
> **pbpersson said:**
> Is there a high water mark in Ubuntu?  In other words, where do you look to see the highest amount of swap you have ever used since the OS was first installed?

not that I know of

' swapon -s ' shows swap usage, so if you'd save that value to a file, then on regular intervals (cron ?) check if usage is higher that what's recorded in the file, and if so, update it, you'd have a very rough high water mark thingie.

---

### Post by Austin25 on 2010-03-30
> **_h_ said:**
> Drive space has nothing to do with it. Swap space is used when your physical RAM is depleted, and your system starts using swap to act as RAM.
Yes, but it is a designated part of the hard drive that is used.

---

### Post by julianb on 2010-03-30
If you don't have too many windows open at once, you can run Ubuntu very well with RAM + swap partition total space of 1GB.

If you want to be able to have 15 windows open at a time, you may need more. 

It is possible to make a system run very well with 1GB ram and no swap, or 2GB ram and no swap. If you have less than 1GB ram, I recommend adding swap space until you have at least 1GB of ram+swap.

---

### Post by aysiu on 2010-03-30
If you have 128 MB of RAM, having a 256 MB swap partition can make a really big difference, performance-wise.

I have a 16 GB SSD and 2 GB of RAM, so there is no swap partition on my drive. I need every byte on that SSD.

---

### Post by cgroza on 2010-03-30
> **aysiu said:**
> If you have 128 MB of RAM, having a 256 MB swap partition can make a really big difference, performance-wise.

I have a 16 GB SSD and 2 GB of RAM, so there is no swap partition on my drive. I need every byte on that SSD.

With that memory it is advised to have at least 512mb swap partition because on my 256 ram machine i always have 300mb swapping.

---

### Post by chucky chuckaluck on 2010-03-30
and speaking of idiot, it took me two days to figure what the thread title meant. very sad...

---

### Post by doas777 on 2010-03-30
I'm a touch dyslexic, so the title didn't make sense until I read it aloud. give it a try, it often helps.

---

