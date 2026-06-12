---
title: "xen reset guest root password"
date: 2008-11-17
forum: Virtualisation
---

### Post by unclecameron on 2008-11-17
I need to reset a root password on a xen guest DOMU, does anyone know how to reset it some other way besides remounting the vm and chrooting into it? I'm not confident I know the commands involved in doing that. Otherwise, does someone have the commands I need to use?

---

### Post by tedly on 2009-07-07
This is how i did it on my centos xen install. This may or may not work for you depending on how your domU is setup.

 1009  xm destroy dungeon 
 1010  xm list 
 1011  cd / 
 1012  ls 
 1013  cd xen/ 
 1014  ls 
 1015  losetup /dev/loop0 /xen/dungeon.img  
 1016  fdisk -l /dev/loop0 
 1017  kpartx -a /dev/loop0 
 1018  vgchange -ay VolGroup00 
 1019  lvs 
 1020  ls /mnt/ 
 1021  ls /mnt/bicketyt 
 1022  mount /dev/VolGroup00/LogVol00 /mnt/bicketyt 
 1023  ls /mnt/bicketyt/ 
 1024  cd /mnt/bicketyt/ 
 1025  ls 
 1026  chroot . /bin/bash 
 1027  pwd 
 1028  umount /mnt/bicketyt/ 
 1029  cd 
 1030  umount /mnt/bicketyt/ 
 1031  vgchange -a n 
 1032  kpartx -d /dev/loop0 
 1033  losetup -d /dev/loop0 
 1034  lvs 
 1035  xm create dungeon 
 1036  xm list 
 1037  xm console dungeon

---

