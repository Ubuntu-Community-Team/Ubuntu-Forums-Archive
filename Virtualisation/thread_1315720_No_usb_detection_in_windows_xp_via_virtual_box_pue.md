---
title: "No usb detection in windows xp via virtual box puel"
date: 2009-11-05
forum: Virtualisation
---

### Post by karimruan on 2009-11-05
Okay, I have the latest version of vbox puel, and it won't recognize ANY usb devices. I enabled USB in the vbox settings for my xp installation. I know it gives me the option to add usb filters, and I think that this is my problem. Can anyone point me to a step by step on getting USB working in 9.04?

---

### Post by karimruan on 2009-11-05
UPDATE:

I added myself and root to the group usbfs, also added us to group usbuser,
still nothing. VB always tells me no usb devices are attached! What do I do?
Please, if someone can help me find the right how to (I have tried almost everything!) I will be eternally grateful!

EDIT:

Using VBoxManage list --long I get the following output:

```

mat@mat-laptop:~$ VBoxManage list --long usbhost
VirtualBox Command Line Management Interface Version 3.0.10
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Host USB Devices:

UUID:               ce2de905-739b-47e1-9346-d42fd9d45936
VendorId:           0x0c45 (0C45)
ProductId:          0x62c0 (62C0)
Revision:           82.22 (8222)
Manufacturer:       Chicony Electronics Co., Ltd.
Product:            HP Webcam
SerialNumber:       SN0001
Address:            sysfs:/sys/devices/pci0000:00/0000:00:04.1/usb2/2-2//device:/dev/bus/usb/002/002
Current State:      Unavailable

UUID:               9e2e32e4-d666-49cf-b1f0-5dcefc580bea
VendorId:           0x192f (192F)
ProductId:          0x0416 (0416)
Revision:           2.0 (0200)
Product:            USB Optical Mouse
Address:            sysfs:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-4//device:/dev/bus/usb/003/015
Current State:      Unavailable


```

It says my USB ports are unavailable. Any ideas?

---

