---
title: "MacBook Air backlight controls don't work 15.04 daily (3.19) but work great on 14.10"
date: 2015-03-28
forum: Ubuntu Development Version
---

### Post by Markus_Iofcea on 2015-03-28
Hi all,

the Ubuntu live image (daily 26.03.2015) of 15.04 has a problem with the backlight keys of my Macbook air (2015). I suspect that there is an issue with the kernel 3.19. 

The keys worked on this macbook with 14.10 and also with kernel versions till at least 3.17.x.

Any way I can get them working on 15.04 with 3.19 or is this is more general issue with 3.19 on many laptops?

/Markus

---

### Post by Markus_Iofcea on 2015-03-28
[FONT=arial]The problem is that there are two backlight directories.

/sys/class/backlight/acpi_video0/
 /sys/class/backlight/intel_backlight/

I created '/etc/X11/xorg.conf.d/20-intel.conf' and filled it with: 
    [B]
   [FONT=courier new]Section "Device" 
   Identifier  "card0" 
   Driver      "intel" 
   Option      "Backlight"  "intel_backlight" 
   EndSection[/FONT]
[/B]
Looks like X prefers the acpi_video0.[/FONT]

---

