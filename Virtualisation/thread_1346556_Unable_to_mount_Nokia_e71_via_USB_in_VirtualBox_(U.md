---
title: "Unable to mount Nokia e71 via USB in VirtualBox (Ubuntu 9.10)"
date: 2009-12-05
forum: Virtualisation
---

### Post by zsugiart on 2009-12-05
halp!

I used to be able to do this up to 9.04, but this is broken in 9.10. 

When I plug in my Nokia e71 into Ubuntu, I used to be able to then mount this in VirtualBox. From within my VM-XP, I can then run PC nokia Suite to sync my calendars and everything else. 

However in 9.10, in VirtualBox my Nokia e71 is only shown in grey, meaning that it can't be mounted. 

Not sure what to be done to make this happen? 

When I connct e71 in PC suite mode, dmesg | tail yield this result:
[http://pastebin.com/m37101b5b](http://pastebin.com/m37101b5b)

Any help / pointer is much appreciated.

---

### Post by zsugiart on 2009-12-05
More info: 
The device is listed in lsusb: 

```
$ lsusb | grep Nokia
Bus 006 Device 004: ID 0421:00ab Nokia Mobile Phones E71 (PC Suite mode)
```

So why isn't my e71 shown either in the file system, and why is it marked as being unavailable in VirtualBox!?

---

### Post by zsugiart on 2009-12-05
The command "VBoxManage list usbhost" yields:

```

UUID:               6487f2b3-3d27-4d38-a1ca-3dacfaff43ac
VendorId:           0x0421 (0421)
ProductId:          0x00ab (00AB)
Revision:           1.0 (0100)
Manufacturer:       Nokia
Product:            Nokia E71
Address:            sysfs:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2//device:/dev/bus/usb/006/002
Current State:      Unavailable

```

... hmm why is it marked 'Unavailable' ?

---

### Post by fouadatmeh on 2009-12-05
Hello,

I have tried it on my e50 mobile and it worked in the guest, but I noticed that my USB-Parallel converter was grayed out!

I found on another forum that running VirtualBox as root solved the problem:
> [http://www.linuxquestions.org/questions/linux-software-2/virtualbox-usb-device-not-available-to-virtual-machine-fc7-586575/](http://www.linuxquestions.org/questions/linux-software-2/virtualbox-usb-device-not-available-to-virtual-machine-fc7-586575/)

I tried it and now I could select the USB-Parallel converter for the guest. the same forum also gives a solution (which I didn't try as I don't need printing in my guest)

Hope that helps

---

### Post by zsugiart on 2009-12-06
Wow thanks for that. I started VirtualBox as root and I could mount my e71 properly. However I don't need to do this back in 9.04 - what was changed?

---

