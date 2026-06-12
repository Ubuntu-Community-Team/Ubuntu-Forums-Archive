---
title: "iphone in virtual box"
date: 2010-08-04
forum: Virtualisation
---

### Post by becatron on 2010-08-04
Hey guys, not sure if this has already been posted, but couldn't find it anywhere.

I've just installed the latest virtualbox (3.2.6) and it seems to have usb support (yay!)

I'm running ubuntu 10.04 as host, and windows 7 as guest.

It recognises the iphone in the sense that it makes the "you have plugged in a usb device" noise, and charges the iphone (not sure if that's just from the host though, but it does disconnect it from the host).

How do I get windows 7 (and itunes) to recognise it??

please help

---

### Post by Ginsu543 on 2010-08-04
Have you selected your iPhone from your Devices --> USB Devices menu? On my WinXP-guest/Lucid-host setup, when I select my iPhone on Devices --> USB Devices, my WinXP makes a noise and a window pops up informing that the iPhone is connected. iTunes will then recognize the iPhone.

---

### Post by becatron on 2010-08-05
Hi thanks for your reply :)

Yeah, I select it, it makes the noise and then.... nothing.

any other ideas?

---

### Post by becatron on 2010-08-05
By the way: windows recognises the device in the device manager. It says it's a "apple mobile device", it has a error symbol across it though... I tried updating the drivers but it thinks it's already up to date.

---

### Post by Ginsu543 on 2010-08-06
On my setup, Device Manager says "Apple iPhone" under "Imaging devices." It only says "Apple mobile device" if my iPhone has no OS on it, such as when I'm trying to restore it or upgrade the OS. So perhaps this is not a USB problem but a Windows/iTunes recognition problem. Have you tried uninstalling and reinstalling iTunes with the latest version (9.2.1)?

---

### Post by lensman3 on 2010-08-06
You might go to Oracle and download the free version and compile it.  It has more "stuff" available than the usual install.  I use an XP virtual machine as my itunes tether.

By the way, don't update the iphone OS.  I bricked my iphone when I went from OS3.xx to OS4.  I had to use another computer to install the OS4, then did a restore of my songs, movies, and apps.

---

### Post by bschelst on 2010-08-06
> **lensman3 said:**
> You might go to Oracle and download the free version and compile it.  It has more "stuff" available than the usual install.  I use an XP virtual machine as my itunes tether.

By the way, don't update the iphone OS.  I bricked my iphone when I went from OS3.xx to OS4.  I had to use another computer to install the OS4, then did a restore of my songs, movies, and apps.


I did it without any problems (upgrade from 3.x -> 4.0 -> 4.0.1 -> 4.1 beta2 - > 4.1 beta 3), but you need to set the USB filters correctly.

---

### Post by becatron on 2010-08-08
I tried upgrading to itunes, but the latest version wouldn't open at all, it would just crash whenever I clicked it. 

I'm already running a Virtual Box 3.2.8 which I got from the Oracle/Virtual Box website...

---

### Post by Ginsu543 on 2010-08-08
Do you have hardware virtualization (VT-x) turned on? For iTunes to work in VirtualBox, your processor must support VT-x and you must turn VT-x on in your BIOS. Then, when you set up your virtual machine, you must check the VT-x option on as well. I only mention this because I used to have the same problem of iTunes crashing as soon as I launch it when I didn't have VT-x turned on.

---

### Post by becatron on 2010-08-09
Yeah I do, at this point just gonna give up...

---

