---
title: "Virtualbox 3.2.8, puel version, no USB printer but all other USB devices ok??"
date: 2010-08-23
forum: Virtualisation
---

### Post by jotto! on 2010-08-23
I know a lot of people seem to have issues with getting USB devices to work correctly but this one is weird in that my external usb HDD, a memory stick and even a scanner is picked up on my XP virtual machine but I cannot for the life of me work out how to get the printer to work.
It is listed when I right click the USB icon but is stated to be unavailable. Have tried turning it on and off, turning it on before starting VB, waiting for the virtual machine to be up and running before switching on...still nothing! lol.

Do I need to unmount it in some way from the host machine first?

Any ideas?

```
UUID:               1e0a1e5c-cf8e-4dd2-814b-65a1089a5e96
VendorId:           0x04b8 (04B8)
ProductId:          0x0001 (0001)
Revision:           1.0 (0100)
Manufacturer:       EPSON
Product:            USB Printer
Address:            sysfs:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-1//device:/dev/bus/usb/002/007
Current State:      Unavailable

```

---

### Post by jotto! on 2010-08-23
Set it up as a shared printer on the network in the end.....

---

