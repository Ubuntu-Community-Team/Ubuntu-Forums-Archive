---
title: "Virtualizing Windows 2003 server in Ubuntu, software choice?"
date: 2008-04-03
forum: Virtualisation
---

### Post by bytemind on 2008-04-03
Hi,

Im going mad reading about Xen, vmware and all those other virtualization programs.

I wanna run Windows 2003 server under Ubuntu, what software do i use in my production enviroment?

---

### Post by veloce on 2008-04-09
I use vmware server on ubuntu gutsy with 2003 server and it works well.

---

### Post by kapitikid on 2008-04-09
Hi

I have installed VMWare Server (console 1.05) on Ubuntu Gutsy Gibbon.
Hardware as follows:
HP DL360 G4p Xeon 3.6 2GB . I installed MS2003 std edition as a guest machine and it cannot see the USB Drive resident on the host.
Contrary to the VMWare manual I am unable to alter the usbdevfs path(on the server console).usbdevfs which seems to of been updated in this version of Ubuntu from usbdevfs in /proc/bus/usb to usbfs in /sys/bus/usb/drivers and according to the VMWare virtual machine guide it looks for usbdevfs in /proc/bus/usb by default.
Have tried adding a entry in etc/vfstab to that effect but alas no effect!
Any suggestions:confused:

---

