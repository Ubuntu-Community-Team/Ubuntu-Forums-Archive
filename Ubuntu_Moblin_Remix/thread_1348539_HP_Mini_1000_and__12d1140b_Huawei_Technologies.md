---
title: "HP Mini 1000 and  12d1:140b Huawei Technologies"
date: 2009-12-07
forum: Ubuntu Moblin Remix
---

### Post by nebu on 2009-12-07
I have two systems one a HP Mini 1000 which runs a hp mie os which is based of the ubuntu netbook remix and another laptop with ubuntu 9.04

I have this usb modem which turns up as this when i do a *lsusb*
```
Bus 001 Device 004: ID 12d1:140b Huawei Technologies Co., Ltd.
```

now to use this i use the command
```
sudo modprobe usbserial vendor=0x12d1 product=0x140b
```

after this the file /dev/ttyUSB0 and the file /dev/ttyUSB1 are created in the computer running 9.04 but not the netbook remix....

The netbook remix has kernel version - 2.6.24-22-lpia
The ubuntu 9.04 has the kernel version - 2.6.28.16

how do i solve this problem on the netbook???

---

### Post by nebu on 2009-12-11
bump

---

