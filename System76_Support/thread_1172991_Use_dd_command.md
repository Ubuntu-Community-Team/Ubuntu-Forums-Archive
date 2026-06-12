---
title: "Use dd command"
date: 2009-05-29
forum: System76 Support
---

### Post by DieUbunt on 2009-05-29
Hi

Could somebody help me to use dd or better command for make a image
1:1 of my internal hard-disk to external one?
Is there any command better than dd making conforme copy?
Thanks in advance;)

Here's the scenario. I have a external hard disk mounted as /dev/sdb1 ( hpfs/ntfs filesystem )
I want to make a copy using dd or better command to make a copy of it to another
external hard disk ( or to my /dev/sda1 inside any directory for example /mnt/image).
What is it the right syntax for dd or better command to make this?
Thanks

---

### Post by iponeverything on 2009-05-29
dd if=/dev/sda of=/mnt/image/sda.image

This command will image the entire disk. You want to just image the partition use sda1 instead of sda

You can mount the partitions inside sda.image via loopback using an offset.

---

