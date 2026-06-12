---
title: "qemu savevm location"
date: 2010-08-11
forum: Virtualisation
---

### Post by bonzi on 2010-08-11
How can I find the location of the snapshot created with savevm in qemu?

---

### Post by Jennifer the Hedgehog on 2012-07-03
They are stored in the disk image file. You can print a list running
```
qemu-img snapshot -l <FILENAME>
```

---

### Post by wildmanne39 on 2012-07-05
Old thread closed.

---

