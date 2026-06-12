---
title: "Gnome Display Problems"
date: 2008-03-04
forum: System76 Support
---

### Post by natibo on 2008-03-04
I have a new system as follows:

[INDENT]1 x  	Sable Performance
Options
*Hard Drive : 750 GB SATA II 300 Mbps - 7200 R
+ $180.00
*Hardware Warranty : 1 Yr. Ltd. Warranty and Technica
+ $0.00
*Keyboard and Mouse : Logitech Cordless Desktop EX 110
+ $39.00
*LCD Monitor : 19” LG Widescreen LCD (1440 x 90
+ $235.00
*Memory : 4 GB - 4 x 1 GB - DDR 2 - 800 MH
+ $119.00
*Operating System : Ubuntu 7.10 64 Bit (Gutsy Gibbon
+ $0.00
*Optical Drive : CD-RW / DVD-RW
+ $19.00
*Portable Flash Drive : no flash drive
+ $0.00
*Processor : Core 2 Duo E6750 2.66 GHz FSB 13
+ $210.00
*Speakers : 2.1 - Logitech X-230 - 2 Satelli
+ $49.00[/INDENT]


After several initial problems (machine came partitioned and the partition was so small, X would often not boot: Advanced desktop settings would not work even after doing the "fix") I reinstalled ubuntu 7.10 from a CD and installed the System76 drivers.

From the start, the monitor did not work right.  The screen was fuzzy/staticy.  I changed the screen resolution, and that fixed the problem, except that the login screen was a square (not widescreen) resolution and was still fuzzy.

Last night I tried to change the theme/appearance and the computer flipped out, screen flickering, theme not found, etc.  I had to reboot.  When I rebooted, the screen was fuzzy again and I could not fix it even with a screen resolution change.

The funny thing is, when I boot into a KDE session (kubuntu) everything is fine (except for the fuzzy square login screen).

I reinstalled compiz, played around with the monitor settings, nothing seemed to work.

Lastly, after the reinstall, often when I go to synaptic to sownload it asks me to insert the CD.  How do I load everything from the CD onto the system so I do not have to do this?

Help!!!

---

### Post by natibo on 2008-03-04
I forgot two more items.  How do I turn on the advanced desktop effects in KDE?  How do I configure KDE for automatic updrades.  I need to know this as for the time being I must use KDE.  I am, however, becoming a convert to this desktop configuration.

---

### Post by thomasaaron on 2008-03-04
> when I go to synaptic to sownload it asks me to insert the CD. How do I load everything from the CD onto the system so I do not have to do this?

sudo gedit /boot/grub/menu.lst
Then comment out the line close to the top that says "cdrom" in it.I forgot two more items. How do I turn on the advanced desktop effects in KDE?

> How do I configure KDE for automatic updrades. I need to know this as for the time being I must use KDE.

We don't support KDE. But there are a lot of customers out there using it  Guys?



Regarding the Screen ReSolution, try this:
[http://ubuntuforums.org/showthread.php?t=709508](http://ubuntuforums.org/showthread.php?t=709508)

---

