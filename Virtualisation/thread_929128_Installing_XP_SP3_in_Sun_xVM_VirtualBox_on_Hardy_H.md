---
title: "Installing XP SP3 in Sun xVM VirtualBox on Hardy Host"
date: 2008-09-24
forum: Virtualisation
---

### Post by Kaivik on 2008-09-24
I have an Aopen AK86-L mobo with AMD 64 Athlon 2 x 80GB SATA (1 sata for windows xp dual booter).

I got VirtualBox running, it mounts the Windows XP SP3 iso and the floppy .img (sata drivers - do I need these?) and gets to the formatting of the XP install in the VirtualBox and then starts chewing up processor power and ultimately locks...

Any ideas?

PS:  I just tried again and watched SysMonitor while it formatted.  It used all my RAM then half of my 3.2 gig SwapFile partition before grinding to a halt... even SysMonitor froze.

PPS: I have attempted the same without the floppy mounted sata drivers for an IDE HD setup in the Box

Solution - allocate less RAM for the Box

---

