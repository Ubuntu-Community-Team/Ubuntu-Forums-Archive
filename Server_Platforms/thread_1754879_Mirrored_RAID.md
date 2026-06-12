---
title: "Mirrored RAID"
date: 2011-05-10
forum: Server Platforms
---

### Post by steve keating on 2011-05-10
I have a server that has one drive with Ubuntu already loaded on it. I would like add another drive and then create a mirrored RAID between the two. Could someone point me to a step by step process to do this?

---

### Post by rubylaser on 2011-05-10
You're in luck, the Ubuntu Docs have you covered...
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

---

### Post by a2j on 2011-05-11
> **rubylaser said:**
> You're in luck, the Ubuntu Docs have you covered...
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

thats if you do fresh install. I don't think thats what OP wanted to do. otherwise, its too easy.

---

### Post by YesWeCan on 2011-05-12
Isn't it a matter of creating a degraded RAID1 on the new disk, then copying the old disk contents to it, then booting off the new disk and adding the old disk to the array, then resync?
Also, install Grub to the MBRs of both disks.
(don't forget to add 'bootdegraded=true' to the Grub kernel command line when booting the degraded array or the kernel will refuse to boot)

*A little more detail:*
Back up any crucial data to a safe place before you do anything.

You basically want to set up the new drive exactly how you want the RAID1 to end up, but do it as a degraded RAID1. This is a nice trick because you then make mdadm duplicate everything for you back on to the original disk by a resync.

You probably need to boot of a live CD/USB. Install mdadm and lvm. Format the new disk as one big partition and then create a degraded RAID1 using mdadm, and make an LVM physical volume out of it which you can then make logical volumes (=logical partitions) on. Eg: you may want /root and /home and swap. Once all that is done, you can copy all your old filesystems across to your new partitions, using 'sudo cp -ar'.

Next, reboot off you original disk. Run 'sudo update-grub' to add the new disk OS to the Grub menu. Reboot off the original disk and select the new OS from the Grub menu (add the bootdegraded=true to the Grub kernel line). This should boot the OS on the degraded RAID1. Check the new OS is all present and correct.

You can now use Gparted to reformat your original drive, in the same format as you used for the new drive before making the array with it, and tell mdadm to add it to the array. This should start a resync. You can check progress with 'cat /proc/mdastat'. Once finished, do a 'sudo update-grub' and 'sudo grub-install /dev/md0' (if you called it md0) to make sure Grub's MBR and stage 1 exist in the 1st sectors of both disks.

I think that ought to be it. Test that you can boot of either disk.

---

### Post by rubylaser on 2011-05-13
Yes, this is exactly the gist of it. I use sfdisk to copy the partitions from the current disk to the new one.
```
sfdisk -d /dev/sda | sfdisk /dev/sdb
```
Then create mdadm devices for each partiton on the device and show missing for /dev/sda. Something like this...
```
mdadm --create /dev/md0 --level=1 --raid-disks=2 missing /dev/sdb1
mdadm --create /dev/md1 --level=1 --raid-disks=2 missing /dev/sdb2
mdadm --create /dev/md2 --level=1 --raid-disks=2 missing /dev/sdb3
```
Then, create a filesystem on the new devices. Rebuild the initrd to include the mdadm kernel modules. And, if you need swap, add it to the disk...
```
mkswap /dev/md1
```

Then copy the stuff from your running drive to the new mdadm device.
```
mkdir /mnt/md0
mount /dev/md0 /mnt/md0
cp -aux /boot/* /mnt/md0
sync
umount /mnt/md0

mkdir /mnt/md2
mount /dev/md2 /mnt/md2
cp -aux / /mnt/md2
```

Don't forget to change the mount points in /etc/fstab. Next, reboot, and add your old disk to the arrays.
```
partprobe
mdadm /dev/md0 -a /dev/sda1
mdadm /dev/md1 -a /dev/sda2
mdadm /dev/md2 -a /dev/sda3
```

Finally, setup grub on both disks.

---

