---
title: "mounting xen windows pvhvm snapshot"
date: 2016-05-12
forum: Virtualisation
---

### Post by Benjamin_West on 2016-05-12
Here are the steps I took to attempt to mount my running windows PVHVM snapshot. The goal is to mount our snapshots, or entire /dev/ubuntu-gnome-vg/OpsWVM1, and tar it to a nice compressed file to store on our snap servers.

I followed a combination of these two articles:
[http://wiki.linuxservertech.com/index.php?action=artikel&cat=3&id=152&artlang=en](http://wiki.linuxservertech.com/index.php?action=artikel&cat=3&id=152&artlang=en)
[https://forum.solusvm.com/topic/1785-windows-hvm-backup-via-lvm-snapshot-kpartx-rsync/](https://forum.solusvm.com/topic/1785-windows-hvm-backup-via-lvm-snapshot-kpartx-rsync/)
[http://linux.die.net/man/8/kpartx](http://linux.die.net/man/8/kpartx)

[I]sudo lvcreate -s -L 5G -n OpsWVM1_snap /dev/ubuntu-gnome-vg/OpsWVM1
  Logical volume "OpsWVM1_snap" created

sudo lvscan
  ACTIVE            '/dev/ubuntu-gnome-vg/root' [20.00 GiB] inherit
  ACTIVE            '/dev/ubuntu-gnome-vg/swap_1' [15.99 GiB] inherit
  ACTIVE            '/dev/ubuntu-gnome-vg/monitor' [5.00 GiB] inherit
  ACTIVE   Original '/dev/ubuntu-gnome-vg/OpsWVM1' [80.00 GiB] inherit
  ACTIVE   Snapshot '/dev/ubuntu-gnome-vg/OpsWVM1_snap' [5.00 GiB] inherit

sudo kpartx -av /dev/ubuntu-gnome-vg/OpsWVM1_snap
add map ubuntu--gnome--vg-OpsWVM1_snap1 (252:7): 0 204800 linear /dev/ubuntu-gnome-vg/OpsWVM1_snap 2048
add map ubuntu--gnome--vg-OpsWVM1_snap2 (252:8): 0 167563264 linear /dev/ubuntu-gnome-vg/OpsWVM1_snap 206848

sudo mount -t ntfs /dev/ubuntu-gnome-vg/OpsWVM1_snap /mnt -o force
NTFS signature is missing.
Failed to mount '/dev/mapper/ubuntu--gnome--vg-OpsWVM1_snap': Invalid argument
The device '/dev/mapper/ubuntu--gnome--vg-OpsWVM1_snap' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sudo mount -t ntfs-3g -o loop,offset=$((63*512)),rw /dev/ubuntu-gnome-vg/OpsWVM1_snap /mnt
NTFS signature is missing.
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
[/I]
I was wondering if anyone had any insight as to why this is happening. I feel that our server has been partitioned correctly... I see in gparted that ntfs-3g is installed and available.

If I need to post any additional output just let me know. Thank you!

---

