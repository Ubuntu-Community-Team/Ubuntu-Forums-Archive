---
title: "Upgrade errors -- again...."
date: 2012-09-16
forum: Server Platforms
---

### Post by MakOwner on 2012-09-16
Does this mean when I reboot this box it's going to not going to come back up?  

```

# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.2.0-30 linux-headers-3.2.0-30-generic-pae linux-image-3.2.0-30-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
3 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 50.9 MB of archives.
After this operation, 180 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-30-generic-pae i386 3.2.0-30.48 [38.2 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic-pae i386 3.2.0.30.32 [1,720 B]                                                                                                  
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic-pae i386 3.2.0.30.32 [2,600 B]                                                                                            
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-30 all 3.2.0-30.48 [11.7 MB]                                                                                              
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-30-generic-pae i386 3.2.0-30.48 [986 kB]                                                                                  
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic-pae i386 3.2.0.30.32 [2,596 B]                                                                                          
Fetched 50.9 MB in 16s (3,161 kB/s)                                                                                                                                                                           
Selecting previously unselected package linux-image-3.2.0-30-generic-pae.
(Reading database ... 47437 files and directories currently installed.)
Unpacking linux-image-3.2.0-30-generic-pae (from .../linux-image-3.2.0-30-generic-pae_3.2.0-30.48_i386.deb) ...
Done.
Preparing to replace linux-generic-pae 3.2.0.29.31 (using .../linux-generic-pae_3.2.0.30.32_i386.deb) ...
Unpacking replacement linux-generic-pae ...
Preparing to replace linux-image-generic-pae 3.2.0.29.31 (using .../linux-image-generic-pae_3.2.0.30.32_i386.deb) ...
Unpacking replacement linux-image-generic-pae ...
Selecting previously unselected package linux-headers-3.2.0-30.
Unpacking linux-headers-3.2.0-30 (from .../linux-headers-3.2.0-30_3.2.0-30.48_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-30-generic-pae.
Unpacking linux-headers-3.2.0-30-generic-pae (from .../linux-headers-3.2.0-30-generic-pae_3.2.0-30.48_i386.deb) ...
Preparing to replace linux-headers-generic-pae 3.2.0.29.31 (using .../linux-headers-generic-pae_3.2.0.30.32_i386.deb) ...
Unpacking replacement linux-headers-generic-pae ...
Setting up linux-image-3.2.0-30-generic-pae (3.2.0-30.48) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-30-generic-pae /boot/vmlinuz-3.2.0-30-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-30-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-30-generic-pae /boot/vmlinuz-3.2.0-30-generic-pae
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
Generating grub.cfg ...
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
Found linux image: /boot/vmlinuz-3.2.0-30-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-30-generic-pae
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
error: unsupported RAID level: -1000000.
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic-pae (3.2.0.30.32) ...
Setting up linux-generic-pae (3.2.0.30.32) ...
Setting up linux-headers-3.2.0-30 (3.2.0-30.48) ...
Setting up linux-headers-3.2.0-30-generic-pae (3.2.0-30.48) ...
Setting up linux-headers-generic-pae (3.2.0.30.32) ...

```



Note that no RAID devices exist on the disks in this box...

```


# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       147G  3.4G  137G   3% /
udev            494M  4.0K  494M   1% /dev
tmpfs           201M  296K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            501M     0  501M   0% /run/shm
/dev/sdb1       234G   24G  208G  11% /radio


# fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00074def

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   308594687   154296320   83  Linux
/dev/sda2       308594688   312580095     1992704   82  Linux swap / Solaris

# fdisk -l /dev/sdb

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a4d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   490233855   245115904   83  Linux
# 


```



It did come back up this time, but what is this?

---

