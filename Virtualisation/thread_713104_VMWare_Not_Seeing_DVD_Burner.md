---
title: "VMWare Not Seeing DVD Burner"
date: 2008-03-02
forum: Virtualisation
---

### Post by pemur1 on 2008-03-02
I installed VMWare with Ubuntu as host and XP as guest. For some reason, XP won't recognize my DVD writer. It sees the floppy and the CD writer though. Also, I thought that when I installed VMWare Tools, I'd be able to copy folders/files from Ubuntu into XP. For some reason, this isn't working either. Any assistance would be greatly appreciated.

---

### Post by fjgaude on 2008-03-02
The easiest way to copy, see files from one to the other, is through Shares. Set Ubunut Shares to whatever you wish, then do the same in Windows, through File Explorer.

To get all the USB devices noticed in Windows you have to do this:

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

```

        mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Good to add this line into your guest .vmx file using text editor:
```

mainMem.useNamedFile=FALSE
```

You will have full copy, paste from host to and from guest, and USB device handling capability, drives, scanners, printers, etc.

Let us know how you are doing.

---

