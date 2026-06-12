---
title: "Migrate RAID to new drives with LVM on LUKS on RAID"
date: 2013-12-04
forum: Server Platforms
---

### Post by DiagonalArg on 2013-12-04
I have found [a good description]("http://www.debian-administration.org/article/639/Encrypting_an_existing_Debian_lenny_installation") of migrating from an unencrypted to a LUKS based Debian system.  I would like to confirm that the following steps make sense when mitrating Ubuntu 12.04 from a RAID mirror to another RAID mirror with LVM on LUKS.  The part I am most unsure about is grub's relationship to LVM:


(1) Install cryptsetup in my old system.
(2) Boot to a USB (which has mdadm, cryptsetup and lvm2)
(3) Prepare the new disks: /boot (RAID) and /, swap (LVM on LUKS on RAID)
(4) cp -ax from my old /boot and / into the new ones  
(3) edit mdadm.conf, crypttab and fstab to point to the new UUID's.
(4) chroot into the new system as described [here]("http://help.ubuntu.com/community/Grub2/Installing#via_ChRoot").
(5) grub-install to both new hard drives
(6) update-grub to create grub.cfg, which should take into account mdadm.conf & crypttab.


Questions:


(1) Are 5 & 6, particularly, correct?  Since there is no "lvmtab", will grub know how to handle lvm when it tries to boot?
(2) I already have cryptsetup, but do I need to install lvm2 to the old system?  I hope not, because right now it doesn't know have internet access.


Thanks!

---

