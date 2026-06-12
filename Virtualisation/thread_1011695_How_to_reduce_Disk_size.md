---
title: "How to reduce Disk size?"
date: 2008-12-15
forum: Virtualisation
---

### Post by sai438 on 2008-12-15
Hi,

I'm a VM which is having 8GB of disk space splitted into 2GB files. I wanted to reduce it to 4GB. How can reduce the size without losing the OS?

Thanks in advance,
Sairam

---

### Post by Dedoimedo on 2008-12-15
Did you preallocate the space?

The way I would do it ... Create another 4GB virtual disk. Attach it. Boot from CloneZilla CD (inside virtual machine), image the first hard disk (8GB) and restore it to the second hard disk (4GB), and then remove the first hard disk.

You do not have to delete the file, merely "un-attach" it from the vm configurations.

Dedoimedo

---

