---
title: "Custom image not booting properly"
date: 2011-01-11
forum: Ubuntu Cloud and Juju
---

### Post by oldhoot on 2011-01-11
I've tried building two different custom images using kvm-qemu, one Centos 5.5 and one Ubuntu 10.10.  Both work fine in the kvm environment.  However, when I try to boot them under UEC, they don't start properly.  My cloud is based on 10.10 and here's a representative console output.....

[    3.223148] sd 0:0:0:0: [sda] Write Protect is off
[    3.224479] EDD information not available.
[    3.224526] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.226686]  sda: sda1 sda2
[    3.228257] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.228784] Freeing unused kernel memory: 828k freed
[    3.229460] Write protecting the kernel read-only data: 10240k
[    3.230348] Freeing unused kernel memory: 332k freed
[    3.231125] Freeing unused kernel memory: 1624k freed
Loading, please wait...
[    3.247636] udev[81]: starting version 163
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... [    3.304196] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k6-NAPI
[    3.304957] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    3.305706] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    3.306317] e1000 0000:00:02.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, high) -> IRQ 10
done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... [    3.609831] FDC 0 is a S82078B
[    3.661229] e1000 0000:00:02.0: eth0: (PCI:33MHz:32-bit) d0:0d:35:6b:06:68
[    3.661958] e1000 0000:00:02.0: eth0: Intel(R) PRO/1000 Network Connection
done.
[    8.335677] EXT3-fs: barriers not enabled
[    8.336580] kjournald starting.  Commit interval 5 seconds
[    8.337216] EXT3-fs (sda1): mounted filesystem with ordered data mode
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

---

### Post by kim0 on 2011-01-13
Hi there,
I suspect you're trying to push a full disk image rather than a raw partition (which eucalyhptus will then turn into a disk image). Check out documentation on creating AMIs for EC2, the process for UEC should be exactly the same

I guess you'll need to add /dev/sda1 to your /etc/fstab as well. If you find a good guide for creating ec2 images, can you please paste it in this thread. Let me know how it goes

---

### Post by raymdt on 2011-01-14
Hey,
i found this guide very helpful

[http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-4-%E2%80%93-image%C2%A0management/](http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-4-%E2%80%93-image%C2%A0management/)


you can get the whole document here 

[http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf](http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf)

---

