---
title: "75Mhz, 16 MB of RAM.... What to do?"
date: 2008-06-18
forum: The Cafe
---

### Post by diablo75 on 2008-06-18
I have a friend who is trying to breath some life back into an old Packard Bell Axcel 472CD PC.  It has a 75 Mhz Pentium with 16 MB of RAM.  My hope was to run Damn Small Linux on it, but the BIOS doesn't support CD-ROM booting, only allowing either the Floppy or Hard Drive as the only devices for that.

We're wanting to:

1.  Wipe the Hard Drive.
2.  Put some form of Linux in place of Windows 3.11.

What can be done?

---

### Post by bubba_169 on 2008-06-18
[http://www.damnsmalllinux.org/install_from_floppy.html]("http://www.damnsmalllinux.org/install_from_floppy.html")
[http://www.damnsmalllinux.org/network-install.html]("http://www.damnsmalllinux.org/network-install.html")

These might be what you're looking for... :D

---

### Post by zmjjmz on 2008-06-18
Google these
Smart Boot Manager
BasicLinux (I'll give you this link [www.basiclinux.com.ru](www.basiclinux.com.ru))
I know it may seem impossible, but...
Damn Small is actually too much for that thing. You'll really prefer BasicLinux.

EDIT: Basiclinux fits on 2 floppies, so you won't need Smart Boot Manager.

---

### Post by LaRoza on 2008-06-18
Try FreeDOS + OpenGEM?

---

### Post by zmjjmz on 2008-06-18
Too little for this, but...
LaRoza, how well do you think that would run on 3MB RAM?

---

### Post by Havoc on 2008-06-18
You could just take the HDD, install it on another machine with a bootable CD-ROM drive, install DamnSmallLinux on that HDD and then put it back to the original machine.

Linux *is* feasible on such a machine. I run Linux with IceWM everyday on an HP Jornada equipped with a 133MHz SH3 CPU (equivalent to a 75MHz Pentium CPU) and 16 or 32MB of RAM. It runs great.

---

### Post by LaRoza on 2008-06-18
> **zmjjmz said:**
> 
LaRoza, how well do you think that would run on 3MB RAM?

I have no idea, sorry. I haven't had a chance to play with a computer that low spec.

FreeDOS is like DOS, so it could run that (it is running DOS now), and the other is just a GUI like WINDOWS.EXE.

---

### Post by cmay on 2008-06-18
my old minix computer has 100mhz 16mb ram. 
it seem it only finds the 8.
you could try minix.

---

### Post by cmay on 2008-06-18
> 
it seem it only finds the 8.

that i should have written as finds the 8mb ram.
 
i also forgot to mention the hard disk is less than 800 mb
so minix doesnt need that much to run .

its also very fun to play whit :)

---

### Post by Yes on 2008-06-18
I've got BasicLinux running on my 75 MHz, 8 Mb i486 and it's great.  DSL was way too big for me, I doubt you'll have much more luck.

---

### Post by ghindo on 2008-06-18
There's a pretty good thread in [Other OS Talk](http://ubuntuforums.org/forumdisplay.php?f=147) about operating systems for really old computers:

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by zmjjmz on 2008-06-18
> **Yes said:**
> I've got BasicLinux running on my 75 MHz, 8 Mb i486 and it's great.  DSL was way too big for me, I doubt you'll have much more luck.
I thought the Min. requirements for it were 12MB RAM, so I assume you're not using X?

---

### Post by Yes on 2008-06-18
> **zmjjmz said:**
> I thought the Min. requirements for it were 12MB RAM, so I assume you're not using X?

I boot it from DOS, so that brings the minimum requirements down to 3 Mb RAM.  X runs, but there's a lot of lag with Abiword and of course I can't run a graphical browser, so there's no reason why I would.

---

### Post by zmjjmz on 2008-06-18
Hm, maybe you could look into running a bunch of terminal apps.

---

### Post by init1 on 2008-06-18
> **cmay said:**
> that i should have written as finds the 8mb ram.
 
i also forgot to mention the hard disk is less than 800 mb
so minix doesnt need that much to run .

its also very fun to play whit :)
Minix will run with less than 100MB I believe

> **zmjjmz said:**
> Too little for this, but...
LaRoza, how well do you think that would run on 3MB RAM?
It will probably work.

---

### Post by zmjjmz on 2008-06-18
640K on a 286?
I'm serious about this. It runs MS-DOS 4, but I want something that isn't crap.

---

### Post by wolfen69 on 2008-06-18
try and get another stick of ram and you will be able to run dsl no problem.

---

### Post by LaRoza on 2008-06-18
> **wolfen69 said:**
> try and get another stick of ram and you will be able to run dsl no problem.

I am not sure, but that computer may not use SIMMS or DIMMS. They may be DIPs or SIPs.

---

### Post by Yes on 2008-06-19
> **zmjjmz said:**
> 640K on a 286?
I'm serious about this. It runs MS-DOS 4, but I want something that isn't crap.

You're only going to be able to run DOS, and AFIAK the only free version of DOS is FreeDOS, which is a MS-DOS clone.  So I'm afraid you're stuck.

---

### Post by bufsabre666 on 2008-06-19
> **LaRoza said:**
> I am not sure, but that computer may not use SIMMS or DIMMS. They may be DIPs or SIPs.

what did you call me?

---

### Post by LaRoza on 2008-06-19
> **bufsabre666 said:**
> what did you call me?

Nothing.

DIMM's and SIMM's are the modules used for installing ram (DIMM's are used now, SIMM's are older). SIP's and SIP's are like the little black chips you see on a DIMM, but separate. To install them (assuming they aren't soddered) you have to fill a row (a "bank") with the appropriate ones. Their "legs" are easy to bend, and they have a way of creeping out of their sockets. The ability to upgrade them is limited as they take a lot of space and are often not removable.

---

### Post by bufsabre666 on 2008-06-19
> **LaRoza said:**
> Nothing.

DIMM's and SIMM's are the modules used for installing ram (DIMM's are used now, SIMM's are older). SIP's and SIP's are like the little black chips you see on a DIMM, but separate. To install them (assuming they aren't soddered) you have to fill a row (a "bank") with the appropriate ones. Their "legs" are easy to bend, and they have a way of creeping out of their sockets. The ability to upgrade them is limited as they take a lot of space and are often not removable.

it was a joke, i should of know you cyborgs with you logic databases wouldnt get jokes

---

### Post by LaRoza on 2008-06-19
> **bufsabre666 said:**
> it was a joke, i should of know you cyborgs with you logic databases wouldnt get jokes

We try, but it is illogical.

---

### Post by Tundro Walker on 2008-06-19
75mhz w/16mb ram!  Holy crap!  That thing will haul butt while playing Ultima 6!  Or Ultima 7 for that matter!

---

### Post by el_ricardo on 2008-06-19
ubuntu lite. I've had it on my old laptop (700MHz/256MB) but apparantly you meet it's minimum specs almost exactly (75MHz/32MB) so maybe with some tweaking you could get that working

---

### Post by Jophish on 2008-06-19
I infact run linux on a computer with 4mb of ram, and a 66mhz processor. I use it often for browsing the internet with links. By the way, its on a nintendo DS.

---

### Post by zmjjmz on 2008-06-19
4mb...
3mb... :/

---

### Post by madmetal on 2008-06-19
like i said to another similar thread Minix3 for testing and hacking purposes..
[http://wiki.minix3.org/wikis/minix3/HardwareRequirements](http://wiki.minix3.org/wikis/minix3/HardwareRequirements)

---

### Post by MONODA on 2008-06-19
I think you could get CRUX onto something like that with TWM. Or maybe LFS :D

---

### Post by cookieofdoom on 2008-06-19
I'd hang parts of it up as decorations. There's just no rescuing some hardware. I suppose it could be used as a file server if you put a decent sized hard drive in it... but it would probably be a bit slow.

---

### Post by D-EJ915 on 2008-06-19
> **zmjjmz said:**
> Too little for this, but...
LaRoza, how well do you think that would run on 3MB RAM?
OS/2 2.1 crawls on my 16MHz 386sx with 4MB, so avoid that, plus it needs 19 floppies to install...that's the only reason I still have it on there, it took so long to get it on.

---

