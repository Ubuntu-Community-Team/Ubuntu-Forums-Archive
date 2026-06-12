---
title: "QEMU KVM crash; APPPORT fills /TMP, / filesystem no longer mounts at boot"
date: 2013-10-24
forum: Virtualisation
---

### Post by DrJohn999 on 2013-10-24
13.04 server: several KVM/QEMU VMs running. Attempted to attach a USB-2 device to one of them which crashed KVm/QEMU. Apport picked it up, and then proceeded to fill the / partition in /tmp with core dumps at 8G each. Now the / partition no longer is found does not mount at boot -- proceeding to repair from a thumb drive boot. What a nightmare! Plan to remove and purge apport at next opportunity. Fortunately this is a test system but reinstall will be a PITA. Stable? I don't think so.

Anyone else seen this kind of runaway between KVM and apport?

---

### Post by DrJohn999 on 2013-10-25
Booted into 13.10 from thumb. This is a LVM on RAID type of installation. Installed mdadm, was able to --assemble all of the RAID pairs, and the VG/LVM configurations were automatically detected. Able to mount and list /root (as well as all of the others); all checked out clean with fsck. Root is about 20% full due to some more apport dumps in /tmp, but nowhere near full.

Went back to boot into recovery mode from installed drives; dropped into Busybox with "/dev/mapper/VG0-root does not exist" error. BUT, 

(initramfs) ls /dev/mapper

shows that VG0-root is there, and

(initramfs) mount -t ext4 /dev/mapper/VG0-root /root

mounts with no problem. Can read root from here, so why is root not mounting at boot-time? It appears as if the MD / LVM configuration now is not coming up soon enough to avoid the timeout, but this is the first time that's ever happened.

Also noted that prior to the timeout while booting, a number of errors like 

Error: via seeking device "/dev/dm-7" to 18447695855040495 

and

uudevd[144]: timeout: killing 'watershed sh -c' /sbin/lvm/vgscan; /sbin/lvm vgchange -a y'' [518]

before it gives up and drops to busybox. This would point to a disk problem perhaps, certainly with bringing up LVM.

Suggestions are much appreciated.

---

### Post by DrJohn999 on 2013-10-26
Restored boot-ability by repairing Grub-2, but still getting the "Error: xxx Seeking Device..." messages during recovery mode boot. Noted that initramfs and associated pckgs had been flagged for upgrade but was not performed at the time of the problems, now have been upgraded.

Really pretty much at a loss how this happened (full / partition kills Grub??), but will stagger on...

---

