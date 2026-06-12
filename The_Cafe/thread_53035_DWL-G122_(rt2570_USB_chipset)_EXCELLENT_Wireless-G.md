---
title: "DWL-G122 (rt2570 USB chipset): EXCELLENT Wireless-G card!"
date: 2005-07-29
forum: The Cafe
---

### Post by jdong on 2005-07-29
[http://www.compusa.com/products/product_info.asp?product_code=318646&pfp=srch1](http://www.compusa.com/products/product_info.asp?product_code=318646&pfp=srch1)

This is a really nice wireless card that I'd recommend to anyone seeking a wireless card for 54M 802.11G networks. Better yet, you can get it for 20 bucks at CompUSA, but this expires THIS SATURDAY!! Even without the rebates, I still would buy the card. It's worth every penny.

Many things make this card special. First of all, it's USB! You can put it on a desktop or laptop. It looks like a USB Thumb Drive, so it's compact, and it also comes with a little extension cradle, so you can move it around and fix it somewhere other than way behind your desktop for the best signal and speed. Its range is just as good as my enterprise-class Cisco card, and beats every other Wireless card I've used, PCI, PC Card, or otherwise. It also does all the encrypting and processing by itself, without taxing the host computer like most wireless cards do (at peak transfers, over 20% of your CPU time can go into processing wireless packets!)

Currently, I'm getting 36Mbit transfer rates at my room, where three other wireless cards I've used don't even pick up the signal!

The chipset maker, RATECH, is fully committed to Linux, and has released Open-Source GPL sourcecode for all its chipsets, including this USB card. In fact, one of the Linux magazines had a sidebar this month about the RT chipset and their dedication to open-source. (The USB source code was just released by RATECH in May, so it's still a bit rough around the edges, but nevertheless still works fine!) Unlike Atheros (madWIFI) chips, these don't have a closed-source HAL to deal with (the entire driver is GPL'd), these drivers stand a great chance of entering a future Linux kernel and working out-of-the-box completely!

FreeBSD 6.0 will have this in the GENERIC kernel, so it'll be plug&go by the end of August!


NOTE: I'm talking about revision B1, which is what you get if you buy it now. The older revision, A2, is based on the Prism54 USB chipset. This is also supported under Linux, but the way the Prism drivers work, you need a full kernel source tree, the prism patch, and a full recompile... The rt2570 drivers for the B1 just need linux-headers and build-essentials.

---

### Post by heimo on 2005-07-29
Sounds great. Just out of curiosity, do you use WEP or WPA? Over a year ago I bought some 3Com 802.11b/g card, which supported both on hardware, but in Linux and W2K only WEP was available.

I love the idea that some manufacturers begin to see the benefits of open source.

---

### Post by WildTangent on 2005-07-29
my friends been looking for a good USB adaptor for a while now, ill make sure i point him towards this thread.

-Wild

---

### Post by GeneralZod on 2005-07-30
More info about the driver development:

[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

I own a 167g (another "G" USB, small form-factored "card" with the same chipset), but the official drivers will crash my computer every so often :( I haven't tried the fixed drivers from the guys above yet, though - they're supposed to be a lot more stable and featureful.  When I set up my MythTV PVR, I'll use these wireless pens to transfer stuff as I won't have any PCI cards to spare.

It's great to see a company do something like this - we should probably set up a "Thanks, ralinktech!" webpage somewhere and have every one who's bought a card on the strength of its commitment to the GPL sign it, so Broadcomm et al can see see what they're missing.  Or at least club together and send a gift basket ;)

---

### Post by jdong on 2005-07-30
Well, I did say it's a bit rough :). For example, bringing the card down and back up will cause a kernel panic, but there's no problem with unplugging and pluging it back in for restarting the interface. Also, there must be a 5 second or so delay between association and the first transmitted packet, otherwise the interface will not function until you unplug and plug it back in.

Seeing how this driver is **1 month old**, I'm extremely impressed with the rt2x00 project's progress and RALinktech's involvement :). This is definitely a lot more reliable than ndiswrapper-powered cards already, and shows GREAT promise for the future.

---

### Post by Brunellus on 2005-07-30
[QUOTE=jdong]Well, I did say it's a bit rough :). For example, bringing the card down and back up will cause a kernel panic, but there's no problem with unplugging and pluging it back in for restarting the interface. Also, there must be a 5 second or so delay between association and the first transmitted packet, otherwise the interface will not function until you unplug and plug it back in.

Seeing how this driver is **1 month old**, I'm extremely impressed with the rt2x00 project's progress and RALinktech's involvement :). This is definitely a lot more reliable than ndiswrapper-powered cards already, and shows GREAT promise for the future.[/QUOTE]
 Did you remember to update the wikipage about wireless hardware support?  This is the sort of thing that should go on there...

---

### Post by macgyver2 on 2005-07-31
Checked it out...then ordered one.  Thanks for the heads up!

---

### Post by Omnios on 2005-07-31
Thanks jdong im in the process of getting a used laptop from a laptop referbisher that someone in my family knows and this will save me a lot of leg work. Had no idea what to look for. Looks sweet

---

### Post by audax321 on 2005-08-15
If anybody can, please respond to this thread and help me out. I can't seem to get the thing to work: [http://www.ubuntuforums.org/showthread.php?p=303192#post303192](http://www.ubuntuforums.org/showthread.php?p=303192#post303192)

Nevermind, problem fixed... check there if you have a similar problem.

---

### Post by macgyver2 on 2005-08-21
I randomly decided to check out Ralink's site and noticed they have their own source code posted.  Incidentally, they posted an update just last Friday (19 August).  Anyway, I'm curious if any of you tried the code off the their site.  Up until now I've been playing with the stuff from the rt2x00 project...hadn't even been to Ralink's site, though now that I'm there I think I'm gonna drop them a thank you.

---

### Post by jdong on 2005-08-22
[QUOTE=macgyver2]I randomly decided to check out Ralink's site and noticed they have their own source code posted.  Incidentally, they posted an update just last Friday (19 August).  Anyway, I'm curious if any of you tried the code off the their site.  Up until now I've been playing with the stuff from the rt2x00 project...hadn't even been to Ralink's site, though now that I'm there I think I'm gonna drop them a thank you.[/QUOTE]
rt2x00 pulls the GPL'd drivers  from RaLink and improves upon it. You get a much better experience and support community by using rt2x00 drivers.


The kernel panics have been associated to PREEMPT (they're working on fixing it), and some issues with sending data before association have been solved in CVS, too. I highly recommend running nightly snapshots as opposed to the beta releases :)

---

### Post by bigdaddydsp on 2005-09-22
I'm using the drivers from the CD w/ ndiswrapper.  Everything seems to work fine but the adapter seems to power off after a couple of minutes of no activity (no lights, no activity, can't bring it back up w/o reboot).  I have fixed this by adding a cron job that pings my router once every minute but this seems like a bandage for the issue.  Do y'all see the same problem with the rt2570 driver?  Should I switch over from the CD drivers to the OSS driver from ralink?

---

### Post by NeoChaosX on 2005-09-24
I'd like to know how to compile this driver in Breezy. The source is demanding to use GCC-3.4 (specifically, the kernel headers are asking for it), and I'm wary of that since the rest of the system is compiled in GCC-4.0.

---

### Post by jdong on 2005-09-24
apt-get install gcc-3.4


"CC=gcc-3.4 make"

---

### Post by zenwhen on 2005-09-24
Does this play nicely with wpa_supplicant? I was thinking about getting rid of the one wire left on my network. I can't give up wpa though.

---

### Post by jdong on 2005-09-24
It definitely supports WPA through on-chip encryption (iwpriv sets key)

---

### Post by Spug on 2005-10-23
Okay, I'm thinking of purchasing this card for my soon-to-be-Breezy desktop computer. If I do, I'll buy it from a Norwegian web shop, however, but I can't see if this is the old or new revision: [http://www.psdata.no/ps.asp?it=108273&mlevel=050800](http://www.psdata.no/ps.asp?it=108273&mlevel=050800)

Is there anything there that tells me if it's the new or old card? I'd far prefer not to have to recompile the kernel and all. I've sent an e-mail to the shop as well, but haven't received a reply before the weekend. Maybe in the beginning of next week.

---

### Post by gd505 on 2005-12-24
I have this USB wireless adaptor and it works. But it was a pain to get working. Also when I use amule and leave it on all night, the wireless adaptor seems to turn off after 1 or two hours = no amule. Does anyone else have this problem.
How did you fix it?

Thank you

---

### Post by m@rcel on 2009-03-17
Hi All

I confirm that card is excellent, the only one problem is the disconnection after 2 hours when Amule is turned on.

Someone know how resolve the problem?

very tanks in advance

Marcel

---

