---
title: "Ubuntu 8.04 server not detecting seagate 2Tb Hard Drive"
date: 2011-05-05
forum: Server Platforms
---

### Post by Hazardr on 2011-05-05
Hi

I have an Asus p5g41t motherboard with a 1TB samsung HDD as the maina and a 2TB western digital Green HDD as the secondary. Its working fine (althought the WD is quite slow when it comes to samba but thats a seperate issue).

I recently purchased a Seagate 2TB green hdd and added it to my server running Ubuntu 8.0.4 fully with kernel 2.6.24-29 and it detects in the bios perfectly fine but when in Ubuntu, nothing shows up when doing "sfdisk -l". It still only shows sda and sdb.

my server is fully upgraded and it has the latest kernel. Any ideas? I tested it in another machine running windows XP and XP sees the Hard drive in Disk Management.

Any help would be greatly appreciated

---

### Post by Hazardr on 2011-05-05
Update:

I tried connecting the hard drive to another machine as the master and booted up Ubuntu 8.04 server installation and it didnt detect the hdd. Is there something I can add to Ubuntu 8.04 to allow for this detection?

---

### Post by tatt on 2011-05-05
Hi Hazardr.

Please can you post the output from 

> fdisk -l

and the output from 

> cat /etc/fstab

---

### Post by Hazardr on 2011-05-05
fdisk - l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062010

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120857   970783821   83  Linux
/dev/sda2          120858      121601     5976180    5  Extended
/dev/sda5          120858      121601     5976148+  82  Linux swap / Solaris

Disk /dev/sdb: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   83  Linux


cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18d022a7-fec0-40c6-bd2f-3296ac8ef139 /               ext3    relatime,error                                                                                                                                                             s=remount-ro 0       1
# /dev/sda5
UUID=121b3d6e-06d0-4579-bf8a-0010760b12c8 none            swap    sw                                                                                                                                                                           0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /home/sdb1      ext3    defaults,errors=remount-ro 0       1root

---

### Post by Hazardr on 2011-05-05
I tried booting with Ubunutu server 11.04 and it detected the hard drive in the installation (unlike ubuntu 8.04). However, I specifically need Ubuntu 8.04 as some apps I use can only work on there. Is there anyway of making it work on there. I'm guessing it has something to do with the kernel

---

