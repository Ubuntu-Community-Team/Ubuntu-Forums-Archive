---
title: "USB support in VirtualBox &amp; Co."
date: 2009-09-15
forum: Virtualisation
---

### Post by Benedolt on 2009-09-15
Hey guys

I have got a quick question regarding USB support in virtualization. I have here a USB mp3 player that doesn't work on linux.

(It's an Odys MP X38 and when I plug it in, the kernel screams "device 
descriptor read/64, error -71" over and over...)

So, I guess I have to resort to using some version of Windows to solve this problem. 
My question is: If I install Windows in a virtual machine (I have been looking at VirtualBox) can Windows access the USB alright or do I have to install Windows on its own partition in order to access the mp3 player.

Your help would be very much appreciated!
-Benedolt

---

### Post by falconindy on 2009-09-15
Yes. USB access can be trickled down into VirtualBox. As long as the device is found by Ubuntu (not necessarily supported), you can create a filter in VirtualBox to pass the device through to the guest OS.

---

