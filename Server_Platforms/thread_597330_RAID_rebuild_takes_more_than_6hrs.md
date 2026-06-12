---
title: "RAID rebuild takes more than 6hrs"
date: 2007-10-30
forum: Server Platforms
---

### Post by honigbluete on 2007-10-30
I have two identical machines IBM x3550 with a hardware RAID1 of two 250GB SATA drives on a ServeRAID. I installed the first one with Ubuntu Server 7.10 (approx. 700 MB on harddisk), took one harddisk out and placed it in the second one to get a mirror of the installation. Now the rebuilding process takes more than two hours by just having 35% completed so it will need at least 6 hours for the whole copy. IMO this is really really slow but I have no experience with this and how long it should take. Is this normal for just 700 MB? I mean, it is not even one percent of the whole diskspace. What if the disk was full? Would it take 250*6hrs? I cannot believe this.

---

### Post by cdenley on 2007-10-30
I don't think it matters how much disk space is used. The RAID controller copies all bytes, not just used bytes. It doesn't see files, only bytes.

---

### Post by insane_alien on 2007-10-30
yeah, it even copies the 'blank' sections as files. this takes time. the bigger the array the longer it takes.

i have a 1TB RAID 5 which i haven't had to rebuild yet and i dread to think how long it would take.

---

### Post by honigbluete on 2007-10-31
Okay, I assume it has to take that long then if really every byte (really byte or maybe sector?) has to be copied. Otherwise RAID developers would have come to any conclusion on how to speed up this process e.g. by just copying the used units. I just expected technology to be much more advanced and take less time.

---

### Post by cdenley on 2007-10-31
I consider it a good thing. Since the RAID controller doesn't attempt to make any sense of the partitioning or filesystem, it will copy any and all data that is written, and there are no compatibility issues.

---

### Post by /etc/init.d/ on 2007-11-01
Did a google for "raid rebuild hours", and, aside from your post, I found this quote:

> "We are beginning to see storage systems with fast RAID rebuild times, taking one to three hours to rebuild 250 GB HDDs [hard disk drives], or even denser,

So it seems as though a few hours is normal.

---

### Post by MJN on 2007-11-01
I don't use RAID so my ignorance of the concept could be the root of my misunderstanding, however should it *really* take this long to rebuild an array?
 
Let's say we have a 250GB disk and, for arguments/clarity sake, the disk is compeltely full. Adding a second disk to mirror this (it is my understanding that RAID 1 is exactly this - a relatively simple mirror) running at a very modest, say, 20MB/s transfer rate would take 250000 / 20 = 12500 seconds = 3.5 hrs to transfer (I am assuming this is what a rebuild entails).
 
So why is the OP's transfer taking upwards of a predicted 6 hours to complete?
 
Again, I may be missing something major but this surely doesn't sound right?
 
Please do someone explain the error of my ways, if only to satisfy my curiosity!
 
Mathew

---

### Post by /etc/init.d/ on 2007-11-01
Did some more googling.  From here:

[http://kerneltrap.org/node/6877](http://kerneltrap.org/node/6877)

A quote from the kernel sources:

> 
/*
* Current RAID-1,4,5 parallel reconstruction 'guaranteed speed limit'
* is 100 KB/sec, so the extra system load does not show up that much.
* Increase it if you want to have more _guaranteed_ speed. Note that
* the RAID driver will use the maximum available bandwith if the IO
* subsystem is idle. There is also an 'absolute maximum' reconstruction
* speed limit - in case reconstruction slows down your system despite
* idle IO detection.
*
* you can change it via /proc/sys/dev/raid/speed_limit_min and _max.
*/


So it seems by default, you are only "guaranteed" a rebuild rate of a mere 100KB/sec, anything else depends on how busy regular disk I/O is.

The site goes on to say:

> So, increasing this 2 variables can dramatically reduce rebuild time, for example, rebuilding 1Tb raid5 with 3 sata (each 500gb) disks with default settings 100/10000 gives me aprox.rebuild end in 800 minutes. Increasing speed_limit_max to 50000 cut rebuild time to 300 minutes.

So, perhaps OP could try something like this:

```
echo 50000 > /proc/sys/dev/raid/speed_limit_min
```

Edit: I'm not sure if the above should be for _min or _max.  _min makes more sense, but the site says to increase _max.

[http://www.ducea.com/2006/06/25/increase-the-speed-of-linux-software-raid-reconstruction/](http://www.ducea.com/2006/06/25/increase-the-speed-of-linux-software-raid-reconstruction/) recommends setting _min to 50000.

---

### Post by MJN on 2007-11-01
You're probably on to something there.
 
> **/etc/init.d/ said:**
> Edit: I'm not sure if the above should be for _min or _max. _min makes more sense, but the site says to increase _max.
 
From what you've quoted it makes sense for this figure to be the **max** given that it appears the RAID rebuild will transfer at upto this speed automatically when the IO system is otherwise idle. If you were to set the **min** to such a high figure then even when the rebuild is trying to honour the request for IO elsewhere (and hence slow down to allow it to happen) it'd still be hogging the bandwidth given the high min setting.
 
So, I'd say set this as the maxiumum setting or, better still, find out what the current min and max settings are as it may not be applicable to this situation (I do think you're onto something though).
 
Mathew

---

### Post by honigbluete on 2007-11-02
I don't know what you mean with "OP".
Please remember that I have a hardware RAID here, so it is a real RAID controller but no software solution. I experimentally rebooted the machine inbetween and took a look into the config of the RAID controller where no OS is running. At that point I could see that it was just 35% done after 2hrs. I stayed inside the controller BIOS for about 15 minutes and it didn't hurry up. About the same speed as with the running Ubuntu. So changing any files inside Ubuntu won't change a thing.

---

### Post by MJN on 2007-11-02
OP = Original Post(er)
 
Despite it being a hardware RAID controller is there any configuration available for it, or means of adjusting its operation?
 
Edit: Oops - I see you did mention it has config. In which case, are there are settings that may be involved with speed?
 
Mathew

---

