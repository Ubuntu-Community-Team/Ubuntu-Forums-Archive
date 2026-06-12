---
title: "[SOLVED] Windows XP Not Booting After Partition Increase"
date: 2008-12-21
forum: Windows
---

### Post by RookieUbuntuUser58 on 2008-12-21
Decided to get rid of the unallocated space above my Windows partition. So I decided to increase the size of the Windows partition taking over that unallocated space. This moved my Windows partition from /dev/sda2 to /dev/sda1. Now when I try to boot up in XP I get a black screen saying starting up and nothing happens. Any ideas how to fix this?

Here is my boot_info_results.txt file from Ubuntu for troubleshooting help:

---

### Post by caljohnsmith on 2008-12-21
OK, it looks like at least part of the problem is you need to change your menu.lst now that Windows is on sda1 instead of sda2; how about doing:
```
gksudo gedit /boot/grub/menu.lst
```
And then replace your current Windows entry at the bottom with:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and let me know exactly what happens when you select XP from the Grub menu. We can work from there.

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **caljohnsmith said:**
> OK, it looks like at least part of the problem is you need to change your menu.lst now that Windows is on sda1 instead of sda2; how about doing:
```
gksudo gedit /boot/grub/menu.lst
```
And then replace your current Windows entry at the bottom with:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and let me know exactly what happens when you select XP from the Grub menu. We can work from there.

You my friend are a genius. That worked perfectly. Cant believe I missed that little thing. I was changing it to "0" in the boot.ini file not the /boot/grub/menu.lst. Thanks again for the help with XP.

---

### Post by caljohnsmith on 2008-12-21
I'm glad that tweaking your menu.lst is all it took; cheers and have fun with Windows and Ubuntu. :)

---

### Post by RookieUbuntuUser58 on 2008-12-21
> **caljohnsmith said:**
> I'm glad that tweaking your menu.lst is all it took; cheers and have fun with Windows and Ubuntu. :)

Yeah I thought it was gonna be more involved. Glad it was simple though, with your help. 

BTW to get XP to load first would I just have to move that XP part above Ubuntu in the menu.lst.?

---

### Post by caljohnsmith on 2008-12-21
> **boost3d23 said:**
> 
BTW to get XP to load first would I just have to move that XP part above Ubuntu in the menu.lst.?
You could move the XP entry above the Ubuntu entries if you want, but be sure to put the XP entry before the lines:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
But a better way would be to change your "default 0" line, because that gives the number of the OS entry that will get loaded by default. Just remember that Grub's number starts at 0, so:
```
default 0 --> boot 1st OS entry
default 1 --> boot 2nd OS entry
default 2 --> boot 3rd OS entry
...etc.
```
Anyway, hope that helps.

---

