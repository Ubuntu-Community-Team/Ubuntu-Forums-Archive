---
title: "Problem with USB in VirtualBox"
date: 2008-03-08
forum: Virtualisation
---

### Post by noorez on 2008-03-08
I'm having some trouble with USB with VirtualBox. When I first installed virtual box, when I created a virtual machine, I received this error: Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).

I fixed with the solution from :
[http://yoten.blogspot.com/2007/06/virtualbox-usb-error.html](http://yoten.blogspot.com/2007/06/virtualbox-usb-error.html) by adding this to /etc/fstab

none    /proc/bus/usb    usbfs    devgid=1001,devmode=666    0    0 

USB then became available for use. 

I have installed windows xp pro in the virtual box. However, Windows XP pro will not install my external HD properly. The little balloon pop up comes up on the task bar saying that it found a device, but thats pretty much as far as it goes. It doesn't seem to install the external hard drive properly since I cannot access it under My Computer. This is a problem because I cannot use my network card with Windows XP without the network driver which I have on the external.

Can someone help me with this ?

---

### Post by ODF on 2008-03-08
To get your USB to work you'll have to install the non-ose version wich is in the virutalbox website, but since you get the error you must have this version.

In order to make it work you have to enable it in the host, your ubuntu.

[https://bugs.launchpad.net/virtualbox/+bug/156085](https://bugs.launchpad.net/virtualbox/+bug/156085)

I hope it helps.

---

### Post by glennric on 2008-03-08
Follow what ODF says for USB.  However, you won't be able to get direct access to your network card from Windows XP run in a virtual box.  You will only get a passthrough network to your host.  So you won't need the driver anyway.  You need to install the virtual box guest additions and then you will have network access assuming you have your virtual machine set up right.

---

### Post by noorez on 2008-03-08
Should network pass through be enabled by default ?

---

### Post by glennric on 2008-03-08
It should be enabled, but you have to install Virtual Box Guest Editions from within the virtual machine to install the drivers for Windows XP.

---

### Post by noorez on 2008-03-09
Ok, the networking works like you said it would, however, I still have the USB problem. I tried the suggested solution, however, even though it would solve the VERR_FILE_NOT_FOUND error, it still would not allow me to use the USB device in the virtual machine and windows xp. The previous solution I had seemed to work, putting this line in /etc/fstab: 

none /proc/bus/usb usbfs devgid=1001,devmode=666 0 0 

This fixes the VERR_FILE_NOT_FOUND error and I can access the device in the virtual machine windows xp. But, the installing of the external hard drive in windows xp still freezes.

I also noticed something about filters the the USB section of setting up the virtual machine. Do I need to add my device to this section ?

---

### Post by MrKlean on 2008-03-09
Did you make the changes in here ..  /etc/init.d/mountdevsubfs.sh    that it tells you to ??

You have to enable usb in there...go to the #Magic to make section.. and remove the # from in front of the next 4 lines.. then reboot ; )  That might help ya ; )

---

### Post by noorez on 2008-03-09
Still no luck!....My external hard drive still fails to install properly in the virtual windows xp. That icon in the taskbar that tells you its installing new hardware doesn't go away. When i tried going into the Control Panel to "Add new hardware" it said that something else was still installing.

Even worse now, when I went to shut down windows xp, it got up to the screen where it said "Shutting down windows..." but it just hung there and I had to turn the virtual machine off. When i went back to start windows xp again, it doesn't!

---

### Post by noorez on 2008-03-09
I think I've discovered another problem now with USB in VirtualBox. 

Ok heres what happened:

Because windows xp would no longer startup properly I deleted and recreated a new virtual machine for windows xp. This time, when I created the virtual machine, I didn't get the USB error, so I assumed that I had fixed the problem. I added a filter for my external hard drive in the USB filter list. I then went to install windows xp. I put the cd in and it started loading: I got that blue screen, and at the bottom of the blue screen the status bar that shows what components are loading. When it got to "Starting Windows..." it just hung. It didn't go anywhere! So I turned off the virtual machine, and disabled my external hard drive in the USB filter list and guess what...the installer went along fine! I have no idea what happened....

I did another test: I kept the USB device enabled in the filter list and let the installer run to the place where it hangs. I then went to the menu Machine->USB devices. The external hard drive device was checked. I unchecked it the installer unfroze and kept running.

(Whew)!

Can someone help with this problem ?

---

### Post by noorez on 2008-03-14
*bump*

---

