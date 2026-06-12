---
title: "Virtualbox add intergrated webcam Dell 1525"
date: 2008-09-26
forum: Virtualisation
---

### Post by linux6994 on 2008-09-26
I have a Dell 1525 which had Vista, it of course messed up. I have installed Hardy 8.04.1 and Virtualbox 2.0.2, Under Kopete the integrated webcam works great on Yahoo IM. However I am attempting to get the webcam device passed through to the virtual XP machine so that AIM IM can see it.

Any ideas ob how to add this device to virtualbox?

57: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_5a9_2640_noserial_if1
  Unique ID: ncZn.o6FPNxSLOw4
  Parent ID: uIhY.aTl1BF3IEy5
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb3/3-1/3-1:1.1
  SysFS BusID: 3-1:1.1
  Hardware Class: unknown
  Model: "OmniVision Laptop Integrated Webcam"
  Hotplug: USB
  Vendor: usb 0x05a9 "OmniVision Technologies, Inc."
  Device: usb 0x2640 "Laptop Integrated Webcam"
  Revision: "1.00"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Speed: 480 Mbps
  Module Alias: "usb:v05A9p2640d0100dcEFdsc02dp01ic0Eisc02ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #63 (Hub)

---

### Post by cyberplay on 2009-03-09
Did you get it to work?

Have the same machine / problem.

---

### Post by raonyguimaraes on 2010-03-28
I`m also trying ... Hope to solve this problem soon

---

### Post by raonyguimaraes on 2010-03-29
And it's done :D

I installed the last version of Virtualbox 3.1 and added the USB support

Added the lines at the file /etc/fstab
# USB for vmware/vbox
none /dev/bus/usb usbfs devgid=122,devmode=664 0 0

Added my user to the vbox users
sudo adduser raony vboxusers

Then you have to enable the USB support at the settings before you turn on your Virtualbox. When it starts it recognize the webcam drivers automatically and works out of the box :D

Wonderful !!!

---

