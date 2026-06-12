---
title: "Unable to see USB Devices with VirtualBox"
date: 2011-04-18
forum: Virtualisation
---

### Post by bigtoetag on 2011-04-18
VirtualBox platform: Windows XP Host, Ubuntu Guest

Problem: Unable to see any connected USB devices (have tried several)

Specific example:  When I connect an Olimex Debugger to the USB port I can see the device using the VirtualBox Devices->USB Devices pull down menu.  When I view the Olimex debugger by hovering over the text, it shows that the device is "Busy".  When I click on the device, it then shows that the device state is "Captured".  However, when I do a "lsusb" command in a terminal window, it doesn't show the device.  If I take the Olimex debugger to a non-virtualized Ubuntu system and connect it, the "lsusb" command shows the debugger is connected.  Any ideas what might be happening?

Thanks

---

### Post by bigtoetag on 2011-04-18
Was finally able to get this working but don't really know what  permutation make it work.  I ended up installing the Window's drivers  when the dialog boxes came up where as before I would ignore the dialog  box assuming that the Window's drivers didn't need to be installed since  I was trying to get it to work on the guest OS, Ubuntu Linux.  After  installing drivers it still didn't work.  I then went in and disabled  the driver in Window's at which point VirtualBox was unable to see the  device (so I guess you do need the Window's driver installed).  I  reenabled the driver and rebooted and it started working.  One  difference I noted, whereas before VirtualBox would show the device as  captured, now it shows the device as captured AND there is an indication  (a check) that the device is enabled.

---

