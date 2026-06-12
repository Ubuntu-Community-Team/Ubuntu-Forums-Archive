---
title: "Wireless dissapears when I boot Win XP as guest host on Ubuntu"
date: 2012-07-23
forum: Virtualisation
---

### Post by drmiho on 2012-07-23
Hello, 
Can anybody help please. I installed Windows XP under Virtualbox on Ubuntu 12.04 because I could not get the scanner on my Epson Stylus SX125 printer-scanner to work. I needed some scanning to be done so I I asked for help on the forums, but nothing worked so I was forced to install Windows XP to be able to scan documents and photos. Now, another problem surged. After the installation of Windows on virtualbox on my Fujitsu siemens Amilo Li 3710 laptop my Wlan connection worked with the guest system, but when I booted XP the next time, the minute I boot XP the WiFi connection on Ubuntu shuts down, and just dissapears?????? When I right-click the network icon in the panel there is no enable wireless, just enable networking. When I shut down windows wireless pops up again and works as if nothing had happend. I am really puzzled, this did not happen while I was using Linux MInt, and had windows 7 as the guest OS. I tried everything, but everytime I boot windows the wireless just dissapears.
Please help

---

### Post by dcstar on 2012-07-24
> **drmiho said:**
> Hello, 
Can anybody help please. I installed Windows XP under Virtualbox on Ubuntu 12.04 because I could not get the scanner on my Epson Stylus SX125 printer-scanner to work. I needed some scanning to be done so I I asked for help on the forums, but nothing worked so I was forced to install Windows XP to be able to scan documents and photos. Now, another problem surged. After the installation of Windows on virtualbox on my Fujitsu siemens Amilo Li 3710 laptop my Wlan connection worked with the guest system, but when I booted XP the next time, the minute I boot XP the WiFi connection on Ubuntu shuts down, and just dissapears?????? When I right-click the network icon in the panel there is no enable wireless, just enable networking. When I shut down windows wireless pops up again and works as if nothing had happend. I am really puzzled, this did not happen while I was using Linux MInt, and had windows 7 as the guest OS. I tried everything, but everytime I boot windows the wireless just dissapears.
Please help

XP is probably "stealing" the WLAN hardware when it starts, you need to disable that happening.

---

### Post by oldos2er on 2012-07-24
Moved to Virtualization.

---

### Post by z3nhakr on 2012-07-24
is your wifi card usb or pci? check "lspci" and "lsusb" and see where it comes up. if it's usb then check which usb devices are shared in vbox.

---

