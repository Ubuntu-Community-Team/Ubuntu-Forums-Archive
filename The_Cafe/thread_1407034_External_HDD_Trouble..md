---
title: "External HDD Trouble."
date: 2010-02-14
forum: The Cafe
---

### Post by Woolio1 on 2010-02-14
Okay, here's the deal. I went out, purchased a nice Hard drive enclosure, and threw an old Hard Drive from a Macbook Pro in it. Now, on my Ubuntu Netbook, it works fine. I've used it for backup multiple times. However, on my Windows Box, it'll pick up the USB-SATA Bridge, but not the drive itself. I've heard reports of Macintosh Hard Drives having a certain logic chip in them, but I'm not sure if this is the case...

The drive is formatted in FAT32, and currently holds about 30GB of files.

Any idea as to why it doesn't work on my Windows box would be great...

-Ericson

---

### Post by tekkidd on 2010-02-14
because its windows

---

### Post by Woolio1 on 2010-02-14
> **tekkidd said:**
> because its windows

Well dur hur hur. Of course that's the reason, but every other hard drive I've thrown into that case has worked. I'm wondering if it's because it's made by Apple, or if there's some other reason.

---

### Post by mechro on 2010-02-14
How big is the FAT32 partition? I think there's some sort of limit imposed by Windows on FAT32.

---

### Post by The Real Dave on 2010-02-14
Everytime I create a fat32 partition in Windows, its always leaves a few Mb unallocated, so perhaps that could be it? Then again, I've never had a problem reading any of my Linux-created FAT32's in Windows, so I'd presume its the drive.

So paranoia on Apples behalf to prevent people reusing drives?

---

### Post by cariboo on 2010-02-14
I suspect it's probably a driver problem. Check the driver CD that came with your external drive. Every external enclosure I've bought comes with a driver CD.

---

### Post by Woolio1 on 2010-02-14
There wasn't a driver CD... In fact, none of the enclosures I've bought have had driver CDs. I plugged them in, and they just worked. On Mac, Windows, and Linux. 

I'm seriously thinking it's some sort of Apple Paranoia.

---

### Post by GMU_DodgyHodgy on 2010-02-15
it might be because it is Apple. 

I have enabled my wife's Windows machine to see shared folders on my linux desktop - including the external HDD I use for back-up.  This only required installing an additional SAMBA program that enables Windows boxes to see a linux machine on the network.

She can see all shared drives and the Printer that is attached to my desktop.

---

### Post by Swagman on 2010-02-15
iirc FAT32 has a max partition size of 32gb. You haven't exceeded that have you ?

---

### Post by Woolio1 on 2010-02-15
> **Swagman said:**
> iirc FAT32 has a max partition size of 32gb. You haven't exceeded that have you ?

Hmm... 160 - 32 =... 128GB. 

Uh, yeah. I've exceeded it by 128GB.

Time to partition into multiple partitions... I can still choose which one to boot from, right?

---

### Post by mfdc1969 on 2010-05-12
I was just given an old iBook and I ripped the HDD out, thinking I could add it to an external drive enclosure and use it on my laptop running Karmic.

It is a:

[INDENT][INDENT]2002 IBM TravelStar 30GB HDD from an Apple iBook
HDD Model #IC25N030ATC04-0  ATA/IDE

It sys on it, "Apple HDD Firmware 2001."[/INDENT][/INDENT]

It does work with Ubuntu using a cheap external drive case

---

