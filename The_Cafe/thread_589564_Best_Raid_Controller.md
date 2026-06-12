---
title: "Best Raid Controller?"
date: 2007-10-24
forum: The Cafe
---

### Post by songshu on 2007-10-24
dear all,

i need a RAID controller for 3 WD1500 Raptors (+ 1 hot spare) and i really don't have a clue about these things.

anybody suggestion?

---

### Post by Sunforge on 2007-10-24
3Ware have a comprehensive array of hardware accelerated array controllers with broad OS compatibility and drivers.

---

### Post by songshu on 2007-10-24
> **Sunforge said:**
> 3Ware have a comprehensive array of hardware accelerated array controllers with broad OS compatibility and drivers.

thanks, even if not comparing the different brands its quite hard to find the most suitable one.....more expensive is probably better ;) but is there a certain limit to where the performance increase is simply not worth the money anymore? i know any answer will be subjective at least.

i don't really care about the price as long as its money well spend, there is plenty of info on-line but not that easy to get a clear picture...anything other i should considerthat is specific to these kind of disks.

3ware Escalade 9500S-12 would this one be a good choice for  &#8364; 889,91

---

### Post by saulgoode on 2007-10-24
If your machine is Linux-only, I would recommend you use its [software RAID capabilities](http://linux.yyz.us/why-software-raid.html).

---

### Post by songshu on 2007-10-24
> **saulgoode said:**
> If your machine is Linux-only, I would recommend you use its [software RAID capabilities](http://linux.yyz.us/why-software-raid.html).

it is linux only and i have been hapily been doing that with RAID1 and never touching the cheap onboard thingies.

as i understood there is a huge performance increase when using real raid controllers with their own memory etc....compared to software raid

*edit:
but you might be right about spending the money one on some extra processor speed instead, will give this a second tought

---

### Post by Sunforge on 2007-10-24
If you're after Linux compatible RAID controllers try this link:

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

If you want to mess with your head:

[http://itmanagement.earthweb.com/columns/article.php/3354191](http://itmanagement.earthweb.com/columns/article.php/3354191)

If you're after performance a decent hardware raid card with a battery backup for cache will turn your head. On the other hand with the speed of SATA disks and current Intel processors I can't argue with previous comments about Linux (or Windows) RAID.

---

### Post by songshu on 2007-10-24
thanks all for the toughts,
they have been been usefull, i reconsidered the options and have spent the afternoon and evening to re read the manuals.....

not using a raid controller means having another single point of failure less and brings better managebility and data migration options in the long run...the downside that it is slightly slower i might as well compensate with buying the latest quad core....

so software raid it is...

thanks again

---

### Post by mozkill on 2007-12-14
> dear all,

i need a RAID controller for 3 WD1500 Raptors (+ 1 hot spare) and i really don't have a clue about these things.

anybody suggestion?

I would recommend that you setup linux on a single drive first, with the the root partition mounted to that drive.   after you get that setup, connect the other 2 identical drives and set them up in a software raid using linux software, and then mount them as your /home partition (if you know how to do that)

alternatively, the text mode installer should allow you to setup the raid and mount it to /home during install if you are savvy enough to try...

---

### Post by sr20ve on 2007-12-14
What HDD interface will you be using? sata, scsi, sas?

I've always liked LSI controllers. SAS is currently the best interface you can get, very fast and very expandable. The sas protocal, although it's similar to scsi, is much better, because each hard drive gets it's own physical link to the controller, so you won't have issues with noise or timeouts causing other drives on the bus to drop offline.

Some of the features to keep in mind when you're shopping around would be the cache memory size, add in memory is usually better than an integrated memory chip.

Get one with a battery backup so you will be able to use write back caching.

Check what raid levels it supports, sometimes the cheaper ones will only do a raid 0 or 1.

---

### Post by toupeiro on 2007-12-14
Raptor SCSI, IDE, SATA, or SAS?

Personally, i think the HP (Compaq) Smart Array controllers rock, but these are generally server cards (PCI-X) though the newer ones I believe are PCI-e

Adaptec makes a pretty bulletproof SCSI raid controller

LSI-Logic is plenty good for SATA and SAS.

---

### Post by sr20ve on 2007-12-14
> **toupeiro said:**
> 

Adaptec makes a pretty bulletproof SCSI raid controller



I've never liked Adaptec's BIOS. They're usually pretty limited. I've recovered completely hosed arrays before from the BIOS of an LSI card that would not even be possible with an Adaptec.

---

### Post by toupeiro on 2007-12-14
> **sr20ve said:**
> I've never liked Adaptec's BIOS. They're usually pretty limited. I've recovered completely hosed arrays before from the BIOS of an LSI card that would not even be possible with an Adaptec.

ok..  I Never had that problem (a completely hosed array) with my 2940uw's or my 2120S. That might tell you something in itself?  either way, Sorry you had a bad experience.

---

### Post by pjkoczan on 2007-12-14
If you're going to go with HW RAID, use 3ware. They actually have really good Linux support.

---

### Post by sr20ve on 2007-12-14
> **toupeiro said:**
> ok..  I Never had that problem (a completely hosed array) with my 2940uw's or my 2120S. That might tell you something in itself?  either way, Sorry you had a bad experience.

I don't remember the exact models, but the Adaptecs I used to work on a few years back would not allow you to force individual drives online or retag an array. Retagging an array can be a huge life saver if something happens and the meta data on the drives gets lost or corrupted.

---

### Post by toupeiro on 2007-12-14
> **sr20ve said:**
> I don't remember the exact models, but the Adaptecs I used to work on a few years back would not allow you to force individual drives online or retag an array. Retagging an array can be a huge life saver if something happens and the meta data on the drives gets lost or corrupted.

must have been your model.  I really don't know what to tell you about that -- but adaptec is pretty much considered a solid controller in the industry for your run of the mill DAS arrays.  I've supported RAID arrays  from 50GB - 57TB, hundreds of them, for years, and I just never had the things you are describing happen.  I'm not saying it can't happen, obviously it can, but if I had to factor in statistics, they wouldn't be high at all.  RAID is extremely bulletproof if you have a non-faulty controller, reliable hard disks, and you aren't doing things to jeopardize your parity like not keeping online spares (for larger arrays), not replacing failed disks timely, and not having disks of different speeds on the same LUN using controllers that can't compensate for that.  If you are experiencing problems like this (more than once in your career), I would definitely reconsider your choice in controllers and disks.

to the OP, I assume since you are asking for a controller, you are wanting to do more than striping and mirroring (raid 0 and 1), like RAID 3 or better.  If you are not, use your on board controllers if you have them :)

---

### Post by mozkill on 2009-01-05
I use the 3Ware 9650 4-port.  It works great with XP and I am happy with it.  I have to install the drivers after I have booted and installed the system on a IDE drive  since I couldnt figure out how to load the driver during XP setup time.

---

