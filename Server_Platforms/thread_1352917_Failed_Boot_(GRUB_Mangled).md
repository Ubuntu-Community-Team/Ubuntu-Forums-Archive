---
title: "Failed Boot (GRUB Mangled)"
date: 2009-12-12
forum: Server Platforms
---

### Post by dj_penguin on 2009-12-12
Upon booting my server this morning (it doesn't run continuously) I found that I couldn't access the Samba shares.  Being a headless server, I had to dig out an old monitor and connect it up.  Upon connecting the monitor the following messages were displayed.
```
kinit: no resume imgae, doing normal boot....
mount: mounting /dev/disk/bu-uuid/ac67818a-4afa-4a75-b78a-b53758624b2b on /root failed:invalid argument
mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: mounting /sys on root/sys failed: no such file or directory
Taget file system doesn't have /sbin/init
no init found, Try passing init=bootarg
```

I attempted to follow the instructions [here]("https://answers.launchpad.net/ubuntu/+source/grub/+question/63005"), but unfortunately, they are for the old version of GRUB.  In addition, the partition where the grub folder is located (sdc5) does not have an /etc/ folder (which I am very confused about).  Anyway, the output from -fdisk -l is as follows

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbcdfbcdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdc: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37ed37ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7268    58380178+  8e  Linux LVM
/dev/sdc2            7269        7299      249007+   5  Extended
/dev/sdc5            7269        7299      248976   83  Linux

```

sda is the second hard disk which is used to store files.  dsc is the system disk with the OS installed.

Any help would be greatly appreciated.

---

### Post by ian dobson on 2009-12-12
Hi,

Maybe try editing your menu.lst so that the root points to /dev/sda1.

Boot up the server and when the grub menu appears press escape then e to edit the boot line and change the root= line to point to your root (/dev/sda1)

Something like:-
kernel          /boot/vmlinuz-2.6.31-16-generic root=/dev/md0 ro quiet splash noresume ro 


Regards
Ian Dobson

---

### Post by dj_penguin on 2009-12-12
> **ian dobson said:**
> Hi,

Maybe try editing your menu.lst so that the root points to /dev/sda1.

Boot up the server and when the grub menu appears press escape then e to edit the boot line and change the root= line to point to your root (/dev/sda1)

Something like:-
kernel          /boot/vmlinuz-2.6.31-16-generic root=/dev/md0 ro quiet splash noresume ro 


Regards
Ian Dobson
Hi Ian,

Thanks for your reply.  I should have mentioned that I am using Ubuntu 9.10 (server edition), so I have the new version of GRUB, which does not use a menu.lst file.

I tried editing the kernel boot parameters, but to no avail.  I tried your suggestion as well as root=/dev/sdc1, root=/dev/sdc2, root=/dev/sdc5.  Unfortunately, none worked.

Thanks again for your reply.

---

### Post by Jose Catre-Vandis on 2009-12-12
Might help to see the output from **blkid** and the contents of your **/boot/grub/grub.cfg** file. Doesn't immediately look like a grub issue, but lets discount that first. Also, did you "do anything" to the server prior to closing down?

---

