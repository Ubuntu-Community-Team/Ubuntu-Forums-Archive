---
title: "Mount USB in Virtualbox 3.10 on Ubuntu 14.04"
date: 2014-06-09
forum: Virtualisation
---

### Post by bojo on 2014-06-09
Hi Guys,

Since I installed ubuntu 14.04 / Virtualbox 4.3.10 I can not mount a usb to be visible in the virtual machine.
The USB is a GPS and the VM is Windows 7
In the past - when I plug in the USB - it would appear under USB devices in the VM and I can mount it. Now I can not see it at all. It mounts however immediately on the host. 
The extension pack is installed and both usb and usb2.0 are checked under the usb settings for the VM. I also tried to add a filter - the one on the top that includes any USB device but I am still not successful. 

Please help.....

---

### Post by bojo on 2014-06-09
Already fixed. It was the group - added my user to vboxusers and rebooted. Also 14.04 does not come with group management (GUI). Had to install gnome-system-tools.

---

