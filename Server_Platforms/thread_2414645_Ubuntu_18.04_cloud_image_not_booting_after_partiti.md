---
title: "Ubuntu 18.04 cloud image not booting after partition resize"
date: 2019-03-13
forum: Server Platforms
---

### Post by apoz on 2019-03-13
Hi all,

I'm facing a problem trying to boot Ubuntu 18.04 cloud image on KVM. If I try to boot the image as-is, there's no problem and it boots properly.

The problem appears when I try to resize the main partition with virt-resize command (tool from libguestfs-tool package).

When resizing, it seems the partition names are changed and the new resized image is not able to boot (my guess is that the boot mechanism gets confused by the partition name change and it does not know where to boot).

Ubuntu 16.04 cloud images did not have the issue, as they had only 1 partition...

The partitions before the resize:

```
[COLOR=#000000][FONT=&amp]root@host:/wvms# virt-list-partitions wvm-1.img[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sda1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sda14[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sda15[/FONT][/COLOR]

```
The virt-resize command:

```
[COLOR=#000000][FONT=&amp]root@host:/wvms# virt-resize --expand /dev/sda1 wvm-1-orig.img wvm-1.img
[   0.0] Examining alm-oln-onefe-1-vm-orig.img
**********
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] 
Summary of changes:
 
/dev/sda14: This partition will be left alone.
 
/dev/sda15: This partition will be left alone.
 
/dev/sda1: This partition will be resized from 2.1G to 149.9G.  The
filesystem ext4 on /dev/sda1 will be expanded using the 'resize2fs' method.
 
**********
[   3.1] Setting up initial partition table on alm-oln-onefe-1-vm.img
[  11.0] Copying /dev/sda14
[  11.0] Copying /dev/sda15
[  11.1] Copying /dev/sda1
 100% &#10214;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#10215; --:--
[  17.9] Expanding /dev/sda1 (now /dev/sda3) using the 'resize2fs' method
 
Resize operation completed with no errors.  Before deleting the old disk,
carefully check that the resized disk boots and works correctly.












[/FONT][/COLOR]

```

The partitions after:

```
[COLOR=#000000][FONT=&amp]root@host:/wvms# virt-list-partitions -l wvm-1.img[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sda1 unknown 4194304[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sda2 vfat 111149056[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sda3 ext4 160943570944
[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

Is there any way to update the boot partition to boot form sda3 instead sda1?

Would growpart be a better method to resize the partitions?

Thanks![/FONT][/COLOR]

---

### Post by apoz on 2019-03-13
It seems we're not alone with this issue...

[https://news.ycombinator.com/item?id=16304781](https://news.ycombinator.com/item?id=16304781)

---

### Post by darkod on 2019-03-13
I have never done it with virt-resize.

When I needed to extend partition of KVM guest I power off the VM and then use qemu-img to resize the virtual hdd. After that you can resize the partition within the OS and the filesystem.

---

