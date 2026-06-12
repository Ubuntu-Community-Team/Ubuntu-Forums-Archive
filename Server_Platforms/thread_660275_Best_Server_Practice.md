---
title: "Best Server Practice?"
date: 2008-01-06
forum: Server Platforms
---

### Post by johnwillis on 2008-01-06
Hi guys,

I've got a nice little project I'm working on at my secondary school to see if it's possible to give the same level of service from a Linux based server as we get from a Windows 2003 based server.

Here's where I want your advice. I know what RAID is. I've set it up before using our Adaptec cards, but what I wanted to know if how significant the performance drop is if I used MD raid in Linux over our hardware card.

And also, does anyone know if MD raid can do RAID 5 - I've read it'll do 0,1 and 0+1 but nowhere seems to confirm my question.

If it can't is there anything else I can use that's software based and still offers the same redundancy as RAID 5?

Cheers guys,

John

---

### Post by fozy on 2008-01-06
You definitely can run a software RAID 5 in linux.  But one tip is you need to run the boot partition in a non-RAID 5 (e.g. a RAID 1 if you want it mirrored) for GRUB.

---

