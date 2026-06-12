---
title: "VMWare not recognizing USB"
date: 2008-04-21
forum: Virtualisation
---

### Post by mygoogoo on 2008-04-21
System:
VMWare Server 1.0.5 build-80187
Guest system: Windows XP
Ubuntu 7.10 Gutsy

VMWare Server does not recognize USB. I have tried the methods below but with no success. From the VM menu I clicked USB and it doesn't show that USB is available.

While VM is running and Guest (XP Home) is powered on I can plug in a USB thumbdrive and it will be recognized by Ubuntu. It does not show in Guest/VM.

1. I tried this method found here:

[http://kb.vmware.com/selfservice/mic...200%2059220408](http://kb.vmware.com/selfservice/mic...200%2059220408)

To work around this issue, mount USBFS to /proc/bus/usb.

To do this while the host is running, execute the following command as root:
mount -t usbfs none /proc/bus/usb

You need to power cycle the virtual machines after the mount command to have access to available USB devices.

To configure the host to mount USBFS automatically on bootup, add the following line in the /etc/fstab file:

usbfs /proc/bus/usb usbfs auto 0 0

If this line is already present in /etc/fstab, it likely has the noauto option set in the options column (4th column). Change this to auto.

2. I also tried method mentioned in topic: ex:

Find the following lines:
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Unmark them so that look like this:
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Restart and your usb devices will be recognised.

3. I also removed from BIOS, USB 2.0 support, and left the standard USB support for ver 1.1, just for the sake of testing it.

USB devices are fine within Ubuntu. Unfortunately USB not working in VMWare, and this seems to be an issue with quite a few people from what I understand. Hopefully someone has a solution.

Your help is greatly appreciated.

Thank you.

---

### Post by dcstar on 2008-04-25
> **mygoogoo said:**
> 
........
USB devices are fine within Ubuntu. Unfortunately USB not working in VMWare, and this seems to be an issue with quite a few people from what I understand. Hopefully someone has a solution.

Your help is greatly appreciated.


And **exactly** what is listed in VM-Removable devices-USB devices when you have started a VM and plug a USB device in?

---

