---
title: "New to UbuntuServer 7x"
date: 2008-04-03
forum: Server Platforms
---

### Post by jameseastman on 2008-04-03
Greetings.  I have recently decided to take the plunge into Ubuntu Server.  I am formerly a user of Gentoo so some Linux topics are common to me.  For this first server setup I plan to install a base server install the most recent kernel I can find.  The machine I’ll be installing on will have two 80GB SATA drives.  For this install I’d like to RAID1 mirror the drives using software RAID and partition the drives exactly the same.  By this I mean something along the lines of ->

fdisk -l /dev/sda

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          17      136521   fd  Linux raid autodetect
/dev/sda2              18         142     1004062+  82  Linux swap / Solaris
/dev/sda3             143         392     2008125   fd  Linux raid autodetect
/dev/sda4             393       14946   116905005   fd  Linux raid autodetect

AND ….

fdisk -l /dev/sdb

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          17      136521   fd  Linux raid autodetect
/dev/sda2              18         142     1004062+  82  Linux swap / Solaris
/dev/sda3             143         392     2008125   fd  Linux raid autodetect
/dev/sda4             393       14946   116905005   fd  Linux raid autodetect

For the RAID setup I plan to set up ->

mknod /dev/md1 b 9 1
mknod /dev/md3 b 9 3
mknod /dev/md4 b 9 4

mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
mdadm --create /dev/md3 --level=1 --raid-devices=2 /dev/sda3 /dev/sdb3
mdadm --create /dev/md4 --level=0 --raid-devices=2 /dev/sda4 /dev/sdb4

And for my LVM2 controlled LogicalVolume(s) I plan -> 

vgscan
  Reading all physical volumes.  This may take a while...
  No volume groups found
vgchange -a y
  No volume groups found

pvcreate /dev/md4
  Physical volume "/dev/md4" successfully created

vgcreate vg /dev/md4
  Volume group "vg" successfully created

lvcreate –L14G -nusr vg
lvcreate -L10G -nhome vg
lvcreate -L4G -nopt vg
lvcreate –L10G -nvar vg
lvcreate -L2G -ntmp vg

vgs
  VG   #PV #LV #SN Attr  VSize   VFree
  vg     1   8   0 wz--n 554.09G 514.09G
lvs
  LV        VG   Attr   LSize  Origin Snap%  Move Copy%
  distfiles vg   -wi-a-  4.00G
  home      vg   -wi-a- 10.00G
  opt       vg   -wi-a-  4.00G
  portage   vg   -wi-a-  2.00G
  tmp       vg   -wi-a-  2.00G
  usr       vg   -wi-a-  8.00G
  var       vg   -wi-a-  4.00G
  vartmp    vg   -wi-a-  6.00G

I further plan to use Grub as my boot manager.

Now …. Here’s my question.  Where do I find the guide for how to do this at the install of the Ubuntu Server?  Many thanks in advance.

jameseastman

---

### Post by stefangr1 on 2008-04-03
This is a good tutorial:

[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

---

