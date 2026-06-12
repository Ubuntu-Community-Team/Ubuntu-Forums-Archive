---
title: "shared video memory in wine???"
date: 2010-06-30
forum: Wine
---

### Post by Azazel on 2010-06-30
I have an NVIDIA card that has 256mb of RAM on board, but it supports up to 512mb if it borrows another 256mb from the system. Does wine support this shared memory feature? if so how do i utilize it?

I've added the registry key for video memory size and games seem to run best when it is set to 256. If i increase it to 512, there is no difference in performance and no additional system RAM used.

Is there a registry key that i can add to share system memory with my NVIDIA card?

---

### Post by cogadh on 2010-06-30
Its not a matter of Wine supporting it, its a matter of Linux, the drivers and your BIOS supporting it. If they already do, then Wine will just make use of it normally.

---

### Post by Azazel on 2010-07-01
Thanks for pointing me in the right direction cogadh.
Turns out the problem was with the amount of shared memory available.

im going to create a separate post of how i fixed my problem and post the link here

---

### Post by Azazel on 2010-07-01
tutorial:
[http://ubuntuforums.org/showthread.php?p=9534907#post9534907](http://ubuntuforums.org/showthread.php?p=9534907#post9534907)

---

### Post by Azazel on 2010-07-01
in addition to increasing my shared memory size i also added an option to my xorg.conf
```
sudo kwrite /etc/X11/xorg.conf
```
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
    **Option	   "AllowSHMPixmaps" "0"**
EndSection
```

this allows NVIDIA drivers to run more efficiently while using shared memory

I also added a registry key in wine to specify the amount of memory to use
```
regedit
```
HKEY_CURRENT_USER > Software > Wine > Direct3D
right click > New String Value
name the string VideoMemorySize
double click on VideoMemorySize
enter the amount of memory to use in megabytes
ok

---

