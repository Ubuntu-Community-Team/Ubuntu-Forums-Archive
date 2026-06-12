---
title: "External Hard drive read only starting from Ubuntu 21"
date: 2022-03-12
forum: Ubuntu Development Version
---

### Post by flxb2 on 2022-03-12
I have several encrypted external hard drives. No problems at all in all my ubuntu 14, 16 and 20 laptops.

Starting from ubuntu 21, one of the SSD just connects as read only. The others have no problems so far.

Ubuntu 22 has the same problem. Something odd is when i connect any hard drive, if i see any file properties, it shows a number(group id) in the group. In the other lubuntu versions is displayed the user name. I tried all the tricks to change group id and the problems is still there.

The SSD with the issues is an ADATA SU800. No problems in HDD's and another SSD's (SU 480)

The problem is general. Tested in Lubuntu, Xubuntu, Kubuntu.

Something I have to do?

---

### Post by colin-i on 2022-03-13
What is the drive format? If it is ntfs and the package ntfs-3g is installed then I don't know what is the problem. Maybe ownership.

---

### Post by jimmy-frydkaer on 2022-03-13
Who is the owner of the troubled drive? If owner i root it'll be mounted read-only for any other regular user, you might need to chmod the drive

---

### Post by flxb2 on 2022-03-20
The only format is ext4 for encrypted disks

---

### Post by flxb2 on 2022-03-20
All the three disks have the same owner. Not difference at all except for model.

---

### Post by colin-i on 2022-03-22
Another possibility is that the disk is counterfeited, but I don't think is in this case. These drives had an erroneous declared size. The test tool is **f3probe** from **f3** package.

---

