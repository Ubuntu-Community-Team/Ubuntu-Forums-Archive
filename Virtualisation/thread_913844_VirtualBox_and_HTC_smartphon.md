---
title: "VirtualBox and HTC smartphon"
date: 2008-09-08
forum: Virtualisation
---

### Post by mmesh on 2008-09-08
Hello!

I'm trying to get HTC Trinity (P3600) to connect to Windows XP SP3 guest OS and do a sync.
I have USB enabled in settings and HTC is listed in USB devices list (down right in status bar of Virtualbox window) but it can-t be checked.
Output of command "VBoxManage list usbhost" is:
VirtualBox Command Line Management Interface Version 1.6.6
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Host USB Devices:

UUID:               3ba82c59-f2ab-4869-c8a5-079646e29ffc
VendorId:           0x046d (046D)
ProductId:          0xc00c (C00C)
Revision:           6.32 (0632)
Manufacturer:       Logitech
Product:            USB Mouse
Address:            /proc/bus/usb/005/002
Current State:      Unavailable

UUID:               5dd71983-a57a-4358-60b2-576074c3e48a
VendorId:           0x046d (046D)
ProductId:          0xc30e (C30E)
Revision:           1.128 (01128)
Manufacturer:       Logitech
Product:            HID compliant keyboard
Address:            /proc/bus/usb/004/004
Current State:      Unavailable

UUID:               8ca51808-1efa-49fb-07ae-4a4b9b5f95d3
VendorId:           0x08ff (08FF)
ProductId:          0x2580 (2580)
Revision:           6.35 (0635)
Product:            Fingerprint Sensor
Address:            /proc/bus/usb/003/003
Current State:      Available

UUID:               3074f66d-a645-4396-8f96-05d61796aac2
VendorId:           0x0bb4 (0BB4)
ProductId:          0x0b05 (0B05)
Revision:           0.0 (0000)
Manufacturer:       HTC
Product:            Generic RNDIS
SerialNumber:       00269435-4800-0142-5800-0050bf3f5173
Address:            /proc/bus/usb/001/009
Current State:      Unavailable


I also have SynCE engine installed and I tried to unload modules that get loaded when HTC is connected but that didn't help.
I tried to disable "advanced network funcionality" on HTC but no go - the same thing.
VirtualBox is v 1.6.6 installed with apt-get from official repository,
Ubuntu is 8.04/Hardy.

What to do?

---

