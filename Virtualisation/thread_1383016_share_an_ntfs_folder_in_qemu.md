---
title: "share an ntfs folder in qemu"
date: 2010-01-16
forum: Virtualisation
---

### Post by pythonscript on 2010-01-16
How can I share a folder on an NTFS partition with a windows xp guest in qemu? I tried this option:

```
qemu -hda winxp.img -hdb fat:rw:/home/pythonscript/bootshare/SHARED/ -m 512M

```

but when I see the D: drive in windows, it's a VFAT disk that doesn't contain any of my files. The NTFS partition is mounted at /home/pythonscript/bootshare on the host, and I'm trying to share the SHARED folder. Thanks for the help!

---

### Post by pythonscript on 2010-01-18
bump? Anyone have any ideas? Google is giving me nothing on this...Does qemu not support ntfs shares? I'm hoping to do this without using a network share (and therefore reduce the hassle significantly).

---

