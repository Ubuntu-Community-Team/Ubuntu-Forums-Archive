---
title: "Ubuntu VMWare: device claimed by another driver (usbhid)"
date: 2016-02-22
forum: Virtualisation
---

### Post by sujingmeng on 2016-02-22
my host system is ubuntu 14.04 and runing windows 10 in vmware.
I want to debug intel realsense in my virtual machine.
I have change [COLOR=#000000][FONT=&#23435]/etc/modprobe.d/blacklist.conf  with blacklist snd_usb_xxx.
[/FONT][/COLOR]
when I plug realsense in USB, lsmod 's output is not change.
but the virtual machine still can't accept my device, with this message:

The specified device is claimed by another driver (usbhid) on the host operating system. The device might be in use. To continue, the device will first be disconnected from its current driver.

I can not stop usbhid.
 if I rmmod usbhid, my keyboard and mouse blocked.

---

