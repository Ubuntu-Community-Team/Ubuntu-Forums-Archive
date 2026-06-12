---
title: "USB Disk with NTFS"
date: 2011-02-22
forum: Server Platforms
---

### Post by Vegan on 2011-02-22
How good is the 10.10 ability to read NTFS formatted USB disks?

I have 2 USB disks.

I can change the format but prefer not to.

---

### Post by stmiller on 2011-02-22
Reads and writes just fine to NTFS.

Make sure to have this installed:

```
sudo apt-get install ntfs-3g
```

---

