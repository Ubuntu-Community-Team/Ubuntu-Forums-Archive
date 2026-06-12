---
title: "Use LVM disk image for UML"
date: 2008-03-25
forum: Virtualisation
---

### Post by kaig on 2008-03-25
I've got some logical volumes that I use as disks for KVM.

Can I use a filesystem on one of those as a root filesystem for UML?

tia,
Kai

---

### Post by kaig on 2008-03-25
Maybe I should be more specific.

Apparently, if I pass ubd0=/dev/mapper/foo to UML, then it expects to find a fileystem in /dev/mapper/foo.  However, what it finds is something that has a partition table, and one of the partitions in it contains the root filesystem.

Kai

---

