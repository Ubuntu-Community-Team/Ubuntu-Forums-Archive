---
title: "command line help!"
date: 2010-05-12
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-05-12
hi, professionals, I use command '' sudo lsusb '' to figured out my USB drive is on a usb port, which call '' Bus 001 device 003: ID Oa48:5007 I/O Interconnect ''

please teach me how to access my usb drive, I am being crazy!

best appreciate!

:guitar::guitar::guitar:

---

### Post by nmaster on 2010-05-12
its probably auto-mounted to something in /media

look there.

---

### Post by ghost_ryder35 on 2010-05-12
> **AresArtemis1 said:**
> hi, professionals, I use command '' sudo lsusb '' to figured out my USB drive is on a usb port, which call '' Bus 001 device 003: ID Oa48:5007 I/O Interconnect ''

please teach me how to access my usb drive, I am being crazy!

best appreciate!

:guitar::guitar::guitar:
use dmesg to see what ubuntu is identifying it as.  it should be something like sdb, sbc (sda most likley is your internal).

then mount the disk like this assuming the drive only has one partition

```

sudo mount /dev/sdb1 /mnt

```

in case it was not obvious the disk is then mounted to /mnt on your filesystem.  so then you can 

```

ls /mnt

``` 

and your files should be shown

---

