---
title: "Vagrant VirtualBox USB JoyStick Support"
date: 2014-08-28
forum: Virtualisation
---

### Post by jake48 on 2014-08-28
Hi All!


I'm trying to create a Vagrant dev environment and I need to give it the ability to access a USB joystick plugged into the host machine. 
Host: Windows 8.1
Guest: Vagrant's Ubuntu 14.04 base box
VirtualBox: 4.3.15
I have installed guest additions and the extension pack. I have also gone into my Window's registry and deleted the needed file.


I can get it so that VirtualBox captures the device (using a device filter with Vendor ID and product ID specificed) and when I unplug and replug the joystick and run dmesg in the Ubuntu guest and get lines like: usb2-1: new full-speed USB device number 5 using ohci-pci. It also shows up in lsusb.


The only problem is it doesn't show up in /dev/input at all. All I get in /dev/input are event0-4, mice, and mouse0. I tried creating a udev rule with the product and vendor ID and symbolic linking it to a name in /dev/input and the name shows up in /dev/input but jstest fails when I try it.


I'm pretty sure that this has to do with the Ubuntu box that Vagrant provides. Any ideas on how to fix this problem?


Another thing, VirtualBox thinks the OS is 32 bit but I have downloaded, and tell Vagrant to create, a 64 bit guest.

---

