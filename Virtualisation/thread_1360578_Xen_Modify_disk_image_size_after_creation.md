---
title: "Xen: Modify disk image size after creation?"
date: 2009-12-21
forum: Virtualisation
---

### Post by Jekshadow on 2009-12-21
I am running a Xen server, and I had created a VM for rendering large scenes, but now I realize that I need some more disk space in the instance. Is there any way to increase the size of a disk image once it is created. I formatted the image as qcow2.

---

### Post by xOrphenochx on 2009-12-21
> **Jekshadow said:**
> I am running a Xen server, and I had created a VM for rendering large scenes, but now I realize that I need some more disk space in the instance. Is there any way to increase the size of a disk image once it is created. I formatted the image as qcow2.

I had this same question awhile back after I was plagued with the winsxs folder on one of my test servers. Simple answer was no. What I ended up doing was using LVM to manage my VM's disks. It's a little bit more work, but more managable

---

### Post by geekshlby on 2009-12-21
1. Create a backup 
2. Convert the disk image from qcow2 to raw.
[INDENT]qemu-img convert -f qcow2 -O raw diskqcow2.img diskraw.img
[/INDENT]3. Create a file containing all zeros.
[INDENT] dd if=/dev/zero of=zeros.img bs=1024 count=1000000 will create create an approximate 1GB file
[/INDENT]4.  Concatenate your new "disk" to your newly converted raw disk from step 1.
[INDENT]cat zeros.img >> raw.img  Remember >> and not >
[/INDENT]5.  Resize the partition.
6.  Resize the filesystem.

---

### Post by Jekshadow on 2009-12-23
> **geekshlby said:**
> 1. Create a backup 
2. Convert the disk image from qcow2 to raw.
[INDENT]qemu-img convert -f qcow2 -O raw diskqcow2.img diskraw.img
[/INDENT]3. Create a file containing all zeros.
[INDENT] dd if=/dev/zero of=zeros.img bs=1024 count=1000000 will create create an approximate 1GB file
[/INDENT]4.  Concatenate your new "disk" to your newly converted raw disk from step 1.
[INDENT]cat zeros.img >> raw.img  Remember >> and not >
[/INDENT]5.  Resize the partition.
6.  Resize the filesystem.

This will really help, thanks.

---

