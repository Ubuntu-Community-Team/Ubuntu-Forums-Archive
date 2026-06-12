---
title: "A Small trick in burning LiveUSB"
date: 2013-04-25
forum: Ubuntu Development Version
---

### Post by ping-wu on 2013-04-25
I always partitioned my USB into two vfat partitions.  The first partition, usually 1.2G but can be smaller, is for buring the Ubuntu iso.  The second partition can be formatted into either vfat or ext2, is used for storage as a regular USB.

In formatting the second (storage) partition, I often use the following command:

sudo mkfs.vfat /dev/sdb2 -n usb

You can use a different label for the vfat partition.  One advantage of using a label for the storage usb is that I can run a script (stored in the second partition) to soft-link my personal data (such as .mozilla, .thunderbird, ./config, etc) into the Live iso image.

Enjoy!
[HR][/HR]

---

