---
title: "Ubuntu Server 8 - Grub won't install!"
date: 2008-05-15
forum: Server Platforms
---

### Post by Philio on 2008-05-15
I'm trying to install Server 8 and I can't seam to get grub to install properly.

I'm using an LSI Megaraid card with a 3Tb array on it if this is relavent.

Running grub and trying root hd(0,0) chucks error 11
Running grub-install /dev/sda says something like cannot read /boot/grub/stage1

Anyone have any idea how to fix this?!

---

### Post by Philio on 2008-05-15
I've sorted it, for some reason the default partitioning scheme created extended partitions (god knows why!) which grub didn't like, manual partitioning scheme installed just fine. I would have done it manually, however I just want to test the server edition out and play with it for a bit!

---

