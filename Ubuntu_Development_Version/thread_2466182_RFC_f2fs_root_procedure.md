---
title: "RFC: f2fs root procedure"
date: 2021-08-21
forum: Ubuntu Development Version
---

### Post by onflash on 2021-08-21
I finally got around to trying this on impish after setting up a number of other distributions with f2fs root filesystems.

The goal is to come up with something that would be appropriate to run in the datacenter for modern deployment types (i.e., high density VMs with shared backing storage) and maybe also on a PineBook Pro in case they ever get stock back in. :)

Here is the procedure I used to convert an impish system today.  If anyone has feedback on how to improve it or questions on the rationale for any of the steps, I am interested!

[HR][/HR]
Operating Environment: 20GB VirtualBox VM with 4GB RAM

Since this is just for a bootstrap root filesystem, the idea is to minimize the storage utilization (and wear on the Samsung FIT USB flash I was using for testing)  That is the reason for ext2 instead of ext4 for the /boot and / filesystems on the bootstrap system - ext2 doesn't have a journal to constantly write to.   Unfortunately, I didn't notice a way to disable the creation of a swap file in the installer.

Once getting into the installer -

**Minimal install** (don't download updates or install third party software)

Installation type:
  [B]Something else
[/B]
**New Partition Table** > **Continue**
+ 1 MB Primary, beginning of this space,  Reserved as BIOS boot area
+ 512 MB Primary, beginning of this space, ext2 Mount Point: /boot
+ 250 MB Primary, beginning of this space, EFI System Partition
+ 8000 MB Logical, end of this space, ext2 Mount Point: /

**Install Now**, [B]Continue 
[/B]
Follow the usual steps to pick a timezone and create a user

Once the installation finished, reboot and log into the new system

Next, install the tools to set up the f2fs filesystem/partition and run gparted -

```
$ sudo apt install f2fs-tools gparted
$ sudo gparted /dev/sdX
```

In the gparted GUI - 

Click on the free space, create as primary partition,  
 Partition name /, format as f2fs, label root, [B]Add
[/B]
To write it to disk, click the green check to apply pending operations

make a note of the partition device** /dev/sdX5** and exit gparted

Next, deal with the default swapfile to avoid syncing it (also because swap on disk doesn't fit my use cases) -

```
$ sudo swapoff /swapfile
$ sudoedit /etc/fstab (delete the swapfile line and save)
$ sudo rm /swapfile
```

Arrange for the modules to be loaded into initramfs before copying to the target f2fs  filesystem so both sides will have it -

```
$ sudoedit /etc/initramfs-tools/modules
```

  add the following -

```
f2fs
fscrypto
crc32-pclmul
crc32c_generic
crc32c-intel
crc32_generic
libcrc32c

```

Mount it up and start the sync -

```

$ sudo mkdir /f2fsroot
$ sudo mount /dev/sdX5 /f2fsroot
$ sudo rsync -HPXax / /f2fsroot/

```

Once the sync has completed, prepare for chroot -

```

$ sudo mount --bind /dev /f2fsroot/dev
$ sudo mount --bind /sys /f2fsroot/sys
$ sudo mount --bind /proc /f2fsroot/proc
$ sudo mount --bind /run /f2fsroot/proc
$ sudo mount --bind /boot /f2fsroot/boot
$ sudo mount --bind /boot/efi /f2fsroot/boot/efi
$ sudo blkid | grep f2fs
```

 copy the UUID value into the terminal buffer

Set up fstab on the target partition -

```
$ sudoedit /f2fsroot/etc/fstab
```

  ^ change ext2 to f2fs and 'errors=remount-ro' to 'noatime' and UUID= to the UUID for the f2fs filesystem from blkid.  (noatime stops an additional category of constant writes which are unneeded for my use cases)

Access the chroot environment to update its initramfs and get it set up in grub -

```
$ sudo chroot /f2fsroot
$ update-initramfs -u
$ update-grub2
$ exit *(from chroot)*

```

Cleanly unmount the target system's mounts -

```

$ sudo umount /f2fsroot/boot/efi
$ sudo umount /f2fsroot/boot
$ sudo umount /f2fsroot/*
$ sudo umount /f2fsroot
```

reboot the system

In the grub menu, the new f2fs root system is listed as **Ubuntu**

The bootstrap ext2 root system is listed as Ubuntu Impish Indiri (development branch) (21.10) (on /dev/sdX4)

Once system startup has finished, log in and check the filesystems to verify that / is on f2fs:

```

$ df -Th
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  393M  1.4M  391M   1% /run
** /dev/sda5      f2fs    12G  6.0G  6.0G  51% /**
tmpfs          tmpfs  2.0G     0  2.0G   0% /dev/shm
tmpfs          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs  4.0M     0  4.0M   0% /sys/fs/cgroup
/dev/sda2      ext2   462M   69M  370M  16% /boot
/dev/sda3      vfat   235M  5.2M  230M   3% /boot/efi
tmpfs          tmpfs  393M   72K  393M   1% /run/user/126
tmpfs          tmpfs  393M   64K  393M   1% /run/user/1000

```

---

### Post by coffeecat on 2021-08-22
20.10/Impish. *Thread moved to **Ubuntu Development Version**.*

---

