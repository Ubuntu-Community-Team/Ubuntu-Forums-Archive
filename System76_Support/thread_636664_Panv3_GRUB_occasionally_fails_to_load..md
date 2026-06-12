---
title: "Panv3 GRUB occasionally fails to load."
date: 2007-12-10
forum: System76 Support
---

### Post by MrUnicorn on 2007-12-10
Yep, I'm having a GRUB issue on my Panv3 laptop (or at least what might be a GRUB issue).  I was a bit hesitant to post this here as I'm not sure it is something that is related to my System76 hardware, but at this point I've scoured the forums and found nothing that has resolved the issue nor have I found anything that describes the symptoms I'm experiencing.  

So, what is happening is that I'll start up my machine, it will make it through the initial BIOS info screen, then occasionally GRUB will fail to load.  I've read plenty of postings about GRUB producing errors, weirdness, the word GRUB, or a prompt.  I get none of that....All that appears is a flashing underscore in its place.  It does not act like a terminal and it never kicks into GRUB after an extended wait (I've given it 10+minutes just to make sure).

I want to stress the occasionally fails part of the above (toss in the word unpredictable as well).  Most of the time everything loads like a dream.  When it does fail, a Ctrl+Alt+Del restarts the machine and this time around GRUB will load as normal....Ubuntu kicks in...everything fine.  Maybe I should just deal with this, but I have a tendency to pack up and move this and when it fails to boot up every third time (at worst...at best once per 1.5 days) it does feel a bit frustrating. 

The problem has persisted through a complete formatting of the hard disk and re-installation of Ubuntu 7.10 through the alternate CD and a re-installation of GRUB using a terminal via the Ubuntu 7.10 live CD (don't worry...i enjoyed and learned from this!).  In each of these I ran a checksum on the CDs before installing.  Each disc was fine.  

Also, IIRC this problem actually appeared on either the first or second time I ever started up my system.  Both the early occurrence and its persistence through reinstalls have made me wonder if there is something about my hardware this causing this.  It seems to be the only constant.

Again, maybe this has nothing to do with GRUB, but it is definitely involved.  Any advice on what to try next is much appreciated!

Specs if they help:
only running Ubuntu 7.10 (standard)
PanV3
120GB hdd,
Nvidia 8600GT vid,
Core 2 Duo 1.8,
2GB ram,
all the other Panv3 stuff.

---

### Post by thomasaaron on 2007-12-10
It sounds like it's not finding grub. Have you changed any of your BIOS settings? Particular in dealing with hardware autodetection?

---

### Post by octathlon on 2007-12-10
This exact thing happens with my panv3 also.  Once it even happened twice in a row, but usually after restarting (holding down power key to turn off, then turn on again), it will boot normally, so I haven't reported it.  I have not changed any BIOS settings, have not even upgraded to Gutsy - all is still as I received it from System76.

---

### Post by MrUnicorn on 2007-12-10
I disabled quiet boot.  Other than that things are as they came.

Just to make sure:

AHCI Conf - enabled
Legacy USB - enabled
Boot Sequence:  HDD, CD, LAN

Anything else I should be looking for?

---

### Post by DRM_free on 2007-12-10
+1 Here. It almost gave me a heart attack the first time thinking that the laptop went dead. Must be a problem with the hard drive, because once I had a CD that loaded its version of GRUB just fine. After I selected "Boot From Hard Drive", the hard drive's GRUB didn't show up. And no, I haven't touched the BIOS settings at all.

I'd say it happens about once every 20 boots.

---

### Post by Zxaos on 2007-12-12
Me too. I thought it was just me so I didn't bother reporting it.

---

### Post by MrUnicorn on 2007-12-13
Well, it is sort of comforting to know that I am not the only one experiencing this problem.  Maybe a fix can be figured out.  From reading others responses it doesn't seem to be the result of changing BIOS settings.  I keep searching the forums, but have had little luck.  

Any more thoughts on what might be causing this?  How to remedy it?

---

### Post by thomasaaron on 2007-12-13
I'm trying to duplicate it here in the shop, but it happens so seldom that it is hard to reproduce.

Furthermore, when it does happen, there are no logs to look at since it happens before booting!

---

