---
title: "Can someone help me find (or make) a basic OS for this task? (networking)"
date: 2010-09-07
forum: The Cafe
---

### Post by TheOnlyMrK on 2010-09-07
Okay so in basic... I live in the middle of nowhere (look up "Golden Valley, AZ" and see how empty it is if you want) and am dirt poor thanks to financial and medical problems with my parents, so my internet is based on WiFi borrowing. I have a satellite dish modified to be used as a WiFi antenna with a (Ubuntu incompatible out of the box, but install disk has Linux driver) ALFA AWUS036NEH high powered long range WiFi card installed on it, with this setup I'm able to connect to most unsecured WiFi SSIDs within a couple miles. That all is connected to a very old desktop of mine running Windows XP Home which is terribly slow and unstable. (AMD K6-2 500MHz CPU, 512MB DDR100 RAM, AGP - 3dfx video card, PCI - USB 2.0 card, IDE - CD drive, PCI - 10/100 Network card)

Anyways out of the less necessary details... I need a Unix/Linux operating system that can handle the simple task of running in only the RAM, have nothing or very little extra included (I don't really want a full OS with all the extras like Ubuntu has, graphic interface is nice but I have no problems with the command line), and have the simple abilities to list available WiFi networks, connect to them, and bridge the WiFi card to the Ethernet card.

So in basic... I want it to be like this computer isn't even there, I just want it to connect to the internet with the WiFi card, and provide it over the Ethernet to my router while running the most minimal of an OS to allow the computer to save power, run cooler, and keep the network stable. Anyone up to helping me with such a stupid task? Lol

Also to anyone that doesn't like "WiFi stealers" I want to at least add in that when I borrow internet I at least try to conserve bandwidth xP and save the more bandwidth heavy stuff to times when people are normally asleep (torrents set to run from 1am to 5am).

---

### Post by BkkBonanza on 2010-09-07
Cheapest low power solution is one of the Intel Atom based mini-itx boards. You can pick these up on ebay now for $30 used, to $80 new (use the [D510 model]("http://www.logicsupply.com/products/d510mo")). They use much less power than old motherboards - 20W vs 130W. They run Linux super well and perform about the same as a P4 3Ghz. 

You can install miniPCIe wifi on board. And they're small enough to put in a mini case with no fan. These cheaper models won't work as a gateway since they only have one ethernet port but they will do well for your purpose with an external router. More costly models have 2 ports.

Do a minimal install of Ubuntu server on to a usb flash stick, plug it in and boot the whole thing off that. No hard disk. Works very, very well. I know because I'm doing it for my router.

As for stealing wifi? Well, that's your problem, not mine.

---

### Post by TheOnlyMrK on 2010-09-07
> **BkkBonaza said:**
> Cheapest low power solution is one of the Intel Atom based mini-itx boards. You can pick these up on ebay now for $30 used, to $80 new (use the [D510 model]("http://www.logicsupply.com/products/d510mo")). They use much less power than old motherboards - 20W vs 130W. They run Linux super well and perform about the same as a P4 3Ghz. 

You can install miniPCIe wifi on board. And they're small enough to put in a mini case with no fan. These cheaper models won't work as a gateway since they only have one ethernet port but they will do well for your purpose with an external router. More costly models have 2 ports.

Do a minimal install of Ubuntu server on to a usb flash stick, plug it in and boot the whole thing off that. No hard disk. Works very, very well. I know because I'm doing it for my router.

As for stealing wifi? Well, that's your problem, not mine.

The problem with that is I have absolutely no money right now. Otherwise I would just buy a nettop and plug the WiFi card into that. Heck if I had money I'd buy my own internet, I hate "borrowing" internet.

---

### Post by Khakilang on 2010-09-07
You can look at several of this Distro like Tiny Core, Damn Small linux, Puppy linux, Crunchbang and PC linux which I can think of. I test run on my old Pentium 3 PC and its fast. But I forgot which one that copy to RAM and run and some of them fail to detect my USB wifi adapter due to proprietary driver and firmware.

---

### Post by d3v1150m471c on 2010-09-07
if they didn't want it stolen they should have at least put a **** password on it. anyhow, have you consider adjusting vm.swappiness and using something like fvwm-crystal as a desktop manager?

---

### Post by Dayofswords on 2010-09-07
Puppy linux runs all in ram
idk about support for your stuff but it's small, and the iso(latest is [this]("http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-5.1.1/lupu-511.iso")) is only 130MB

> if they didn't want it stolen they should have at least put a **** password on it.
this is just the "girl dressing provocatively is asking to be raped" in different form, which makes no sense

---

### Post by BkkBonanza on 2010-09-07
If you can't buy new hardware then use what you have. 

Install onto your current system. It'll work but cost you about $8/mo. more for electricity... 

If you're asking if Linux can do this - well, yes. Linux is used in a wide variety of wifi routers and small appliances. 

We're Ubuntu users here and Ubuntu can do this too. You don't need a gui desktop. Just do a minimal server install and config and manage it using ssh from your other computer or whatever you're using.

Edit:
It isn't going to matter which Linux you choose. Just go with what is most familiar. If you use Ubuntu on your desktop then use the server version here. Whatever you install will boot off "something" and just sit there feeding data from your usb <-> ethernet. It's not actually doing anything that would use the disk anyway. Just system logs which you can put in RAM if you like.

---

