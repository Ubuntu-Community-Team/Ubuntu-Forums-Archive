---
title: "Issue when resizing Xenial cloudimg"
date: 2016-10-12
forum: Virtualisation
---

### Post by apoz on 2016-10-12
Hi, 

I'm trying to resize the main partition of the Xenial cloud image, and  for some reason it seems when I convert back the image from raw to Qcow2  format the main partition seems gone.

Am I doing something wrong? The new Qcow2 disk should be fine, right?
[I][COLOR=#000000]
#Downloading a Ubuntu Xenial cloud image from official repo[/COLOR][/I]
**wget [https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-disk1.img](https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-disk1.img)**

*#That VM Disk only has 1 partition of 2.2G (I want to extend it to 4G for example)*
**sudo virt-filesystems --format=qcow2 --long --parts --blkdevs -h -a xenial-server-cloudimg-amd64-disk1.img **
Name       Type       MBR  Size  Parent
/dev/sda1  partition  83   2.2G  /dev/sda
/dev/sda   device     -    2.2G  -
[I]
#I create a new raw disk to do the virt-resize[/I]
**qemu-img create -f raw my_ubuntu.raw 4G**

*#Then let's do the resize (it seems to work fine)*
** sudo virt-resize --expand /dev/sda1 xenial-server-cloudimg-amd64-disk1.img my_ubuntu.raw**

[   0.0] Examining xenial-server-cloudimg-amd64-disk1.img
 100% &#10214;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#10215; 00:00
**********

Summary of changes:

/dev/sda1: This partition will be resized from 2.2G to 4.0G.  The 
filesystem ext4 on /dev/sda1 will be expanded using the 'resize2fs' method.

**********
[  33.3] Setting up initial partition table on my_ubuntu.raw
[ 128.4] Copying /dev/sda1
 100% &#10214;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#10215; 00:00
 100% &#10214;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#10215; 00:00
[ 245.0] Expanding /dev/sda1 using the 'resize2fs' method

Resize operation completed with no errors.  Before deleting the old disk, 
carefully check that the resized disk boots and works correctly.

*#the partition is there*
**sudo virt-filesystems --format=raw --long --parts --blkdevs -h -a my_ubuntu.raw **
Name       Type       MBR  Size  Parent
/dev/sda1  partition  83   4.0G  /dev/sda
/dev/sda   device     -    4.0G  -

**qemu-img info my_ubuntu.raw**
image: my_ubuntu.raw
file format: raw
virtual size: 4.0G (4294967296 bytes)
disk size: 4.0G
[I]
#Let's convert this disk to qcow2 format[/I]
[B]sudo qemu-img convert -c -O qcow2 -f raw my_ubuntu.raw my_ubuntu.qcow2
[/B]
*#Let's have a look at the created qcow2 disk*
**qemu-img info my_ubuntu.qcow2 **
image: my_ubuntu.qcow2
file format: qcow2
virtual size: 4.0G (4294967296 bytes)
disk size: 299M
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: false
    refcount bits: 16
    corrupt: false

[COLOR=#ff0000]*#But the partition IS NOT THERE! (at least that is what it seems for libguestfs-tools!)*[/COLOR]
**sudo virt-filesystems --format=qcow2 --long --parts --blkdevs -h -a my_ubuntu.qcow2 **
Name      Type    MBR  Size  Parent
/dev/sda  device  -    4.0G  -
[B]
qemu-img --version[/B]
qemu-img version 2.5.0 (Debian 1:2.5+dfsg-5ubuntu10.5), Copyright (c) 2004-2008 Fabrice Bellard

---

