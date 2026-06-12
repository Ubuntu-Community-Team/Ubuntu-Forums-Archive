---
title: "ESXi Hyperviser, Ubuntu Server and USB Drive"
date: 2010-11-12
forum: Virtualisation
---

### Post by Skavenger0 on 2010-11-12
I've got a ESXi hyperviser with Ubuntu Server 10.10 as a guest.

I've been trying to get Ubuntu to see a USB Drive plugged into the physical server.

I have gone into the Virtual Servers settings and added the USB Controller to the hardware list.

I have also tried adding the recommended solution for vmware workstation by adding:

```

sudo nano /etc/fstab

---------------------------
# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

Ive been checking /dev but only have SDA*
I have also created this as my mount point:
```

sudo mkdir -P /media/flash 
```

Has anyone had any experience/luck this this. I have tried searching the forums etc but everything seems to relate to VMware Workstation.

---

### Post by dcstar on 2010-11-13
> **Skavenger0 said:**
> I've got a ESXi hyperviser with Ubuntu Server 10.10 as a guest.

I've been trying to get Ubuntu to see a **USB Drive plugged into the physical server**.
..........
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
```
Automounting (Ubuntu Server)

By default, **disk drives do not automount in Ubuntu Server Edition**. If you are looking for a lightweight solution that does not depend on HAL/DBUS, you can install "usbmount". 
```

---

### Post by Skavenger0 on 2010-11-15
I'm not trying to get the drive to automount, I cant even see the drive in /dev

---

### Post by whees on 2010-11-19
Passthrough USB is only supported from esx(i) 4.1 and up.

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022290](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022290)

Check with the commands "lsusb" and "dmesg" in your vm to see if ubuntu sees the usb device.

Then mount it!

---

