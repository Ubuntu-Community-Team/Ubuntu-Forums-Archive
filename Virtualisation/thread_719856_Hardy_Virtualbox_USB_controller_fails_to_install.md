---
title: "Hardy Virtualbox USB controller fails to install"
date: 2008-03-09
forum: Virtualisation
---

### Post by hebetude on 2008-03-09
I've applied the 15 different paths to enable USB, but everytime I start up XP it tries to install the USB controller driver .. fails.. and I can't access any USB devices.

I installed the Proprietary Virtualbox from the Gutsy Innotek repos.

My VBoxManage list usbhost looks like this:

```

UUID:               368aa8e5-006a-495c-a0a3-24b34f1743b3
VendorId:           0x046d (046D)
ProductId:          0xc521 (C521)
Revision:           87.1 (8701)
Manufacturer:       Logitech
Product:            USB Receiver
Address:            /proc/bus/usb/004/002
Current State:      Busy

UUID:               ebc28f39-e7ac-4fb4-cf83-05e5f6a69c06
VendorId:           0x064e (064E)
ProductId:          0xa101 (A101)
Revision:           1.0 (0100)
Manufacturer:       SuYin
Product:            HP Webcam
SerialNumber:       CN0314-OV01-VH-R03.02.02
Address:            /proc/bus/usb/007/004
Current State:      Busy

UUID:               5e0a14ca-3e2d-4224-2b9e-79038b36298a
VendorId:           0x046d (046D)
ProductId:          0xc111 (C111)
Revision:           9.41 (0941)
Manufacturer:       Harmony Remote 0-2.6.0
Product:            Harmony Remote 0-2.6.0
Address:            /proc/bus/usb/004/003
Current State:      Captured

```

I even ran VBox within a root session, the same BS happens everytime.  Do I have to reinstall XP? whats the deal here

---

### Post by kyphi on 2008-03-09
No you do not have to reinstall anything.

You will find a solution here:

[http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html](http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html)

---

### Post by yurx cherio on 2008-12-03
I believe I found all posts and recommendations and tried all possible remedies mentioned online:

* created link from /proc/bus/usb/* to /dev/bus/usb as described
* uncommented lines in /etc/init.d/mountdevsubfs.sh
* patched /etc/udev/rules.d/40-permissions.rules
* chmod 777 /proc/bus/usb/0??/0?? (for all devices)
* sudo chown -R root:vboxusers /proc/bus/usb
* patched fstab with "none /proc/bus/usb usbfs devgid=<VBOXUSERS>,devmode=666 0 0"
* tried fstab with "usbfs /proc/bus/usb usbfs devgid=<VBOXUSERS>,devmode=666 0 0"
* tried running VirtualBox as me and root (both in VBOXUSERS group)
* Tried variation having devices in VirtualBox USB Filters list

What's amazing is that  Windows XP can initially see the device, detects it properly (even activesync starts up on both guest XP and my pocket PC) and hangs trying to set up drivers. It happens always regardles of USB device type (thumbdrive, cell phone, external HD, mouse, etc). It almost looks like the device appears to be read-only for the guest OS.

---

