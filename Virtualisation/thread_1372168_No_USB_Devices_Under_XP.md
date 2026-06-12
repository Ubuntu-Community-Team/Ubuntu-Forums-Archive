---
title: "No USB Devices Under XP"
date: 2010-01-04
forum: Virtualisation
---

### Post by ..::| Dave89 |::.. on 2010-01-04
I have VirtualBox 3.1.2 installed under Ubuntu 9.10, running both Kubuntu 9.10 and Windows XP Pro.  USB devices work perfectly under Kubuntu, however not so with XP.  Since the main reason I'm running XP is to manage my iPod and iPhone, and being that they're USB devices, that is a big problem.  Any reasons why USB works under Kubuntu but not XP?

TIA

---

### Post by howefield on 2010-01-04
Not sure why you would have usb ok in Kubuntu but not with XP. Are you getting any USB devices, or is it just the ipod/iphone giving you a problem ?

The basics are, use the Personal Use & Evaluation License (PUEL) version of Virtualbox from virtualbox.org (not the Open Source Edition (OSE) in the repository).

Add yourself to the vboxusers group.

Enable USB devices in the VM settings.

Add a filter for each USB device and you should be ready to go.

You got all that covered ?

---

### Post by ..::| Dave89 |::.. on 2010-01-04
All USB devices (except for keyboard/mouse)

I'm using VirtualBox 3.1.2 installed from the .deb file downloaded from virtualbox site

I've added myself to the vboxusers groups before, still nothing

USB is enabled in the VM settings

I clicked on add filter from device, first time crashed VirtualBox, when restarted,, it said Aborted under the Windows XP entry on the list of VMs, second time didn't crash, but still didn't work.

---

### Post by act28 on 2010-01-04
Have you done this? (See screenshot attached)

---

### Post by act28 on 2010-01-04
Oh... iPod and iPhone. Whoops.
Something to do with the fact that the USB controller is emulated? Not sure.
Make sure the iPod is unmounted from the host first?

---

### Post by Vignesh S on 2010-01-04
Yeah, the USB device can't be mounted in two places at once, so its either mounted in XP or in Ubuntu. Yeah, I think you'll have to manually unmount it before it mounts in XP, though I could be wrong being a newer version of VirtualBox and all...

---

### Post by aranbanjo on 2010-01-04
I got the same problem with a nokia phone.. but I've also tried with a usb pen drive and the result is the same... moreover I've verified and the devices aren't mounted. All the other stuff is installed and configured (i.e. Guest Additions).
As I read in the wiki in Jaunty you had to edit

/etc/init.d/mountdevsubfs.sh

```
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
```

and /etc/init.d/mountkernfs.sh
```

## Mount the usbfs for use with VirtualBox
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=$ID,devmode=664
```

than edit the fstab
```

## Mount the usbfs for use with VirtualBox
domount usbfs usbdevfs /proc/bus/usb -onoexec,nosuid,nodev,devgid=$ID,devmode=664
```

Do you think it's still necessary? 
From my lsusb i can see my device ir recognized, maybe is still not managed by udev?

```
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 064e:a110 Suyin Corp. HP Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 014: ID 0421:041e Nokia Mobile Phones 6680
```

---

### Post by oldgeekster on 2010-01-04
Ever since I switched to Sun Virtualbox 3.1.2x (individual user license) with VboxGuestExtensions installed - am having no difficulty mounting any of my USB devices in a Windows XP virtual machine installed therein. ;)

Your mileage may vary....

---

### Post by aranbanjo on 2010-01-04
Ah ok, everithing solved.

I'v only logout... it needs a reboot o restart the server...

WTF  :lolflag:

---

### Post by howefield on 2010-01-05
> **oldgeekster said:**
> ...am having no difficulty mounting any of my USB devices in a Windows XP virtual machine installed therein. ;)

Such a heartwarming story, the OP is bound to take great comfort from it.
:lolflag:

> Your mileage may vary....

Surely not ;)

---

