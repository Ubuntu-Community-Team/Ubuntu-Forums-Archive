---
title: "buying graphics cards and monitors"
date: 2010-02-24
forum: The Cafe
---

### Post by DavidFourer on 2010-02-24
I am starting this in the cafe because I think it would be a little off-topic in the Ubuntu hardware forum until I have more specific questions.

I am considering upgrading my monitor/graphics/video.  I have been reading about graphics cards and monitors and trying to figure out if I should some day buy a better graphics card with the HDMI cable.  Currently the on-board graphics only supports VGA connection.  

This is what I have now: 
Ubuntu 9.10
HP Pavilion p6100z (desktop)
AMD Athlon LE-1660
nVidia on-board Graphics Processor Geforce 6150SE nForce 430   Memory 512 MB
2GB DDR2-800MHz SDRAM
nVidia (proprietary) driver V.185.18.36
monitor HP 2009m 20-inch 900x1600 res.
  I am getting a similar monitor that is 1920x1080

All the reasonably priced monitors seem to be 1920x1080 res.  I guess that supports the HD video format so that is what they are making today.  They support HDMI, DVI-D, or VGA cables, but my computer only has VGA and a separate audio cable.

If I plugged in a new graphics card, what would happen, as far as Ubuntu recognizing it and my computer functioning with it?  Will it be difficult to make it work?  Assuming it all works right, what's the benefit?  I am reading about these things and I can't really understand what is the benefit.  I don't do games but I watch video - usually Netflix - and do a lot of still photo editing and viewing.

Any tips or links are appreciated.

---

### Post by gsmanners on 2010-02-24
From the hardware specs you have provided, I think your best bet would be a 9500 GT nVidia card (or 9400 if you prefer lower power). That would make use of your driver and you could get up and running right away with just switching to the new monitor. You would also have VDPAU support for playing high def video in Linux [s]once you upgrade to Karmic[/s].

---

### Post by fortguy on 2010-02-26
How is your HP 2009m monitor set up in /etc/X11/xorg.conf? I have the same monitor, but I can't get it configured right.

---

### Post by DavidFourer on 2010-02-26
> **fortguy said:**
> How is your HP 2009m monitor set up in /etc/X11/xorg.conf? I have the same monitor, but I can't get it configured right.
/etc/X11/xorg.conf reads:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```
I don't know what this means.  I just did a new install of Ubuntu 9.10 and it worked.

---

