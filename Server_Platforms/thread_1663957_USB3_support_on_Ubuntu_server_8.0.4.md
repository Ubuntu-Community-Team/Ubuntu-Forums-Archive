---
title: "USB3 support on Ubuntu server 8.0.4?"
date: 2011-01-10
forum: Server Platforms
---

### Post by mathieu_ on 2011-01-10
Hi,

I just bought a dual USB2/USB3 external disk for backup purposes on my Ubuntu server box, running 8.0.4 LTS. For various reasons I can't upgrade to the newest LTS yet and I was wondering if there were any plans for USB3 support on Ubuntu Server 8.0.4?

Cheers,

mathieu

---

### Post by proxess on 2011-01-10
I highly doubt it, seeing that the only kind of support for 8.04 is security support, unless you get it off some kind of backport ppa.

---

### Post by mathieu_ on 2011-01-11
Gee, and I thought "long term support" was actually for that sort of thing, including drivers for new hardware and suchlike...

---

### Post by Thirtysixway on 2011-01-11
> **mathieu_ said:**
> Gee, and I thought "long term support" was actually for that sort of thing, including drivers for new hardware and suchlike...

LTS is only for security and major problems, not adding new features.  You may be able to find some documentation online on how to add support for USB3, but probably wouldn't be compatable with updates from canonical/ubuntu in the future. :\ sorry

Maybe you can find some kernel module(s) that will add support? I'm really not sure.  But it won't be from canonical/ubuntu if you do find them.

---

### Post by mathieu_ on 2011-01-12
Awww...

From the [LTS page]("https://wiki.ubuntu.com/LTS") (Ubuntu Wiki):
[INDENT]we define the LTS to be: [...] **Compatible with New Hardware:** We will make point  releases throughout the development cycle to provide functional support  for new server and desktop hardware. 
[/INDENT]So maybe it's too late in the 8.0.4 cycle to integrate that kind of support? No more "point releases"? Is the development cycle over? :-/

Well, I guess I gotta prepare the migration to the newest LTS...

---

