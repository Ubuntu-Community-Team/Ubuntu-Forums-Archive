---
title: "Ubuntu and Hp ProBook 450 G1 compatibility"
date: 2014-05-20
forum: Ubuntu, Linux and OS Chat
---

### Post by dim4 on 2014-05-20
Hello, 
I didn't find anywhere information about ProBook 450 G1 compatibility with Ubuntu. I would like to know if anyone runs Ubuntu on this notebook model. I interested in dual boot Ubutu 14.04 LTS and Windows 8.1.

---

### Post by ubfan1 on 2014-05-20
The linlap.com site just has a template for this machine, but 4 people have voted on compatibility, and 2 said "good" (one "fair", and one "poor").  Read up on the UEFI issues, and here are some settings on the "linux" line in the grub.cfg file to try if you have video issues:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

Older Intel video card:
i915.modeset=1 or i915.modeset=0
newer:
i915.i915_enable_rc6=1

video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

---

### Post by dim4 on 2014-05-21
Yes, I already saw this site, but there is not enough info about the compatibility. Thank you for the grub.cfg settings info !

---

### Post by dim4 on 2014-05-22
I just installed Ubuntu 14.04 LTS on this HP Probook machine, but there is a big bug - no drivers for WiFi Mediatek 7630e. I thing this is not "compatibility". Do you have any idea how to make WiFi work ???[COLOR=#000000]

[/COLOR]

---

### Post by ubfan1 on 2014-05-22
A bug has  been filed on this wireless: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146)

---

### Post by maxim8 on 2014-06-23
The only way to solve WIFI bug for me was to install another WiFi card - I bought [Intel ® Wireless-N 7260]("http://www.ebay.com/itm/Intel-Wireless-N-7260-Plus-Bluetooth-Single-band-/181443765179?pt=US_Internal_Network_Cards&hash=item2a3ee423bb") - instead of unsupported Mediatek card. However now I am facing problem with headphones and mic - the internal microphone is working well but when I am connecting my headphones with mic it does not recognises my headphones and contunues play sound to speakers.

---

### Post by Bucky Ball on 2014-06-23
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

