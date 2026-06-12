---
title: "powertop disabled usb in virtual box"
date: 2010-06-05
forum: Virtualisation
---

### Post by kmsalex on 2010-06-05
ok i've been using virtual box for a few month's now and have never had this problem before, when i go into a virtual machine and hover over the usb icon it says no usb devises  attached. but if i right click on the icon a list comes up with my web-cam and card reader (as well as my flash drive if i had it plunged in) but i can't select them.
i think this has something to do with using powertop. there's an option to suspend unused usb ports, i think thats the point when usb in virtual box stopped working. but there's no option to disable usb suspend. but every time i lunch powertop the option to enable it is still there.

any ideas on geting usb working in virtual box, by the way i'm using vb 3.2.2 closed sorce.

---

### Post by TheFu on 2010-06-06
Only 1 OS at a time can control a USB device. If the host OS has grabbed the device, then it will not be available in a client OS. I don't know what "powertop" is.  If you can disable powertop until after the VMs are running and have captured the USB devices, I think you'll be able to start it and let it do whatever it wants for the other USB devices.

---

### Post by kmsalex on 2010-06-06
I don't think i necessary understand what your saying. first i said i don't know how to disable what powertop did (by the way it was just a theory that it was the culprit) and i show powertop in the screan shots i posted. in the past I've had usb devices mounted in both host and geust os. again vb detects the usb device but it's grayed out and i can't select it.

---

### Post by kmsalex on 2010-06-06
Ok, found the answer myself, forgot to do this workaround when i installed 10.04...new i would forget something. Found it on a bug on lunch pad
[https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/136549](https://bugs.launchpad.net/ubuntu/+source/powertop/+bug/136549)
and the workaround
[http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

---

