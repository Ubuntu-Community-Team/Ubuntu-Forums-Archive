---
title: "Incorrect partition table"
date: 2017-07-10
forum: Server Platforms
---

### Post by egarrido on 2017-07-10
Hello!

With Ubuntu server 16, with only one disk used as LVM, after some weeks running. I´ve got an incorrect partition table:

```
# fdisk /dev/sda1

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.
/dev/sda1: device contains a valid 'LVM2_member' signature; it is strongly recommended to wipe the device with wipefs(8) if this is unexpected, in order to avoid possible collisions

Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0x11b17dbd.

Command (m for help): ^C
# exit
```

What´s the reason?

---

### Post by slickymaster on 2017-07-10
Thread moved to **Server Platforms** for a better fit

---

