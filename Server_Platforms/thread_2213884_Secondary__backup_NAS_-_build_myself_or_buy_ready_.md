---
title: "Secondary / backup NAS - build myself or buy ready one?"
date: 2014-03-29
forum: Server Platforms
---

### Post by sgofferj on 2014-03-29
In addition to my (remodeled) homeserver, I am thinking of deploying a NAS as backup storage in a different location. The reason is that on my disks basically is my whole life. All photos I ever took, all videos, all documents, etc. etc. etc. Last year, I had a failure of my 2 disk RAID1. Both disks failed within a rather short time, so I didn't even get to buy a spare and let the RAID rebuild before the second disk failed. That and the following months while my disks were at the Seagate Recovery Service were pretty scary! Fortunately, those guys could recover all of my data except one totally unimportant file! I never want to experience that kind of stress again...!
Unfortunately, when talking about terrabytes of data, there is no practical backup solution but using yet another bunch of disks - at least nothing that would be affordable for home use.
So besides the RAID in the main server (which is now gonna be 4 disks and RAID5 or ZFS with RAID-Z2), I was thinking of a second storage unit, i.e. a NAS, which I would deploy in another location, probably the garden-house or the basement, and connect to the main server via a dedicated 1G or 10G connection for replication.

What is the opinion of this forum about the "best" solution? Should I build the NAS system myself or buy something ready-made, such as QNAP, Synology, etc.?
Note that this NAS' only task would be secondary/backup storage so all this stuff like apps and such what you can find on commercial NAS boxes is fairly irrelevant. More important to me is hardware reliability and stuff like recoverability and online replication.

One big plus of a self-built solution I already found out :). There are Mini-ITX sytems which have a single 12V input. For such a system, a UPS solution, even with additional integration of solar energy, would be fairly easy to knit.

---

### Post by TheFu on 2014-03-29
It really comes to your preference.
If you have more money than time, buy.
If you have more time than money, build.
The built solution will have much more capability, very much more flexibility and can start out relatively cheap for what you get.

So .... if you will build, take a look at the FreeNAS forums for their suggested hardware. Prior to reading there, I would have gone in a completely different direction. Just be aware that if you are planning ZFS/RAIDz2 that more RAM is required than expected or performance will suffer.  So the FreeNAS builds have 4-20 disk solutions, including recommended cases and drive bays. It is amazing what $800 can get you if you built it yourself. If you care about performance, be certain to get a quality SAS/SATA HBA. I've seen LSI models that support 16 HDDs for $300.

When HW-RAID devices fail, nothing but a backup will get that data back. The proprietary nature of those devices makes it next to impossible for normal nerds to recover without replacement. Be careful in your choice. Plus the supported HDDs inside these devices is fairly strict. Not just any 4TB HDD can be put inside.

So you have already mentioned this - but just to be certain it is understood by lurkers - **RAID is not a backup.  We still need backups for the 100s of reasons where RAID fails.**

---

### Post by sgofferj on 2014-03-29
Wow, one post, all answers I was looking for!
Thanks a lot! :)

---

### Post by TheFu on 2014-03-29
While I appreciate your vote of confidence in my post, getting some varied opinions can't hurt. 
We are each biased in our answers by our history - I am no different - even if my answer is 100% correct. ;)

I left off the _nerd level_ portion of the solution. If you don't love dealing with this stuff, buy. Reading your signature has me convinced that won't be an issue for you. ;)

OT question.  When is the best time to visit populated areas in Finland?  It was on my list for vacation travel this spring, but I'd like to visit after all the cold, but before it becomes too popular .... high 50s - low 70s (14-22 degC) in temps would be ideal.  Met some Fins in Thailand last fall and they were soooo much fun!

---

### Post by sgofferj on 2014-03-29
Well, your answer contained all information _**I**_ needed (and parts I already figured myself) :).

> **TheFu said:**
> OT question.  When is the best time to visit populated areas in Finland?  It was on my list for vacation travel this spring, but I'd like to visit after all the cold, but before it becomes too popular .... high 50s - low 70s (14-22 degC) in temps would be ideal.  Met some Fins in Thailand last fall and they were soooo much fun!

Well, right now we have about zero at night and +10 - +15°C during day where I live, near Tampere. Helsinki probably is a bit different because it's by the sea. The thing is, Finland is so big and most tourists visit rather the UNpolulated areas, aka. nature tourism, so I don't think, THAT aspect would matter so much. Summer holidays start around midsummer and in Summer holidays, practically everybody is gone somewhere in a hut in the forest, so cities are gonna be very empty. On the other hand, during Summer, there's a million various festivals, mostly Rock, but also other cultural stuff.
Temperature-wise it's probably going to get pretty warm pretty quickly inland. But - as I said - Helsinki always is a bit different.
Actually, you can monitor temperatures and check forecast from one of my projects :D. I run a website for stormchasers with tons on different forecasts :). It's in my sig too :).

---

### Post by HermanAB on 2014-03-29
Well, if you want to have maximum geek fun with your NAS, get a Raspberry Pi or a Beaglebone Black and hook up a couple of USB disks...

---

### Post by houstonbofh on 2014-03-29
I am a big fan of nas4free.  (A fork of Freenas without the corporate behind it...)  However, as TheFu stated, FreeBSD is picky on the hardware.  Go with supported hardware, and quality components.  (This does not mean RAID cards, as they hurt rather than help)  But I have built an enterprise system with 12 hot swap drives, an SSD dedicated ZIL device, and 32gig of ram serving a VMware Horizon View cluster with about 50 desktops, and it is barely ticking over.  And it was Just over $3000, when a comparable NetApp solution was more like $30,000...

---

