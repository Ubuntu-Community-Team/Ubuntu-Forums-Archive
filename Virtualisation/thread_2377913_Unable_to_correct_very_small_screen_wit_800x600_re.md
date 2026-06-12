---
title: "Unable to correct very small screen wit 800x600 resolution only"
date: 2017-11-17
forum: Virtualisation
---

### Post by garyr2 on 2017-11-17
Kubuntu17.04 OS on qemu virtual machine
ATI Radeon HD7450 Graphics card.
Sources.list and associated files are set for stable, restricted, universe and multiverse.

After updating my system, my 1920x1200 screen went to 800x600 and the screen only fills about 50% of the monitor area. Apparently I am supposed to be using the fglrx driver. This driver doesn't exist on my machine. ATI web site indicates that I need to install an AMDCatalyst driver. According to the Ubuntu web page this means that I should install fglrx-install which should install the fglrx dirve (a subset of AMDCatalyst). Unfortunately, apt-get can't find the package. The suggestion that I use "system-settings -> software updates -> Aditional Drivers" doesn't work because "system-settings" does not have a "Software Update" feature. Further, Moen doesn't list drivers. 

How do I get the fglrx driver installed on my system?

garyr2

---

### Post by Bucky Ball on 2017-11-18
[This link]("https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Dropping-fglrx") might shed some light.

---

### Post by wildmanne39 on 2017-11-18
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by garyr2 on 2017-11-18
Correction:
My graphics card is an RS230 but running "lspci -nn | grep -E 'VGA|display'" yields :
"01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos PRO [Radeon HD 7450] [1002:677"

I really need help on this. Pleeeese!

garyr2

---

