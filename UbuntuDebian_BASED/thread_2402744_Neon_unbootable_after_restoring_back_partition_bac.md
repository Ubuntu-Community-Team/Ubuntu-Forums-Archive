---
title: "Neon unbootable after restoring back partition backup"
date: 2018-10-04
forum: Ubuntu/Debian BASED
---

### Post by timonoj on 2018-10-04
Hi guys!

So, I made a backup of the partition before upgrading my Neon. The upgrade didn't go as expected, and before delving into make it workable, I wanted to go back as I needed to do stuff. But now it won't boot, I get only to the Grub greeting bash shell and I'm left there to choose/figure my boot. If I use a USB stick to choose the Linux partition to boot, then I'm shown the proper Grub menu, with all the entries as I left them, and can boot merrily to my KDE Neon.
So...here's my partition table:
> 
(parted) print list                                                       
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  473MB   472MB   ntfs         Basic data partition          hidden, diag
 2      473MB   578MB   105MB   fat32        EFI system partition          boot, esp
 3      578MB   595MB   16.8MB               Microsoft reserved partition  msftres
 4      595MB   84.5GB  83.9GB  ntfs         Basic data partition          msftdata
 5      84.5GB  85.3GB  839MB   ntfs                                       hidden, diag
 6      85.3GB  246GB   161GB   ext4                                       msftdata

As you can see, my ext4 partition is on /dev/sda6. If I perform a grub-install, it seems to get no trouble, but I still fail to boot:
> 
$ sudo grub-install /dev/sda
Installing for x86_64-efi platform.
Installation finished. No error reported.

This is my /boot/efi/EFI path:
> 
/boot/efi/EFI$ ls
Boot  Microsoft  neon  ubuntu

And this is the neon folder:
> /boot/efi/EFI/neon$ ls -ltr
total 3406
-rwxr-xr-x 1 root root     108 Oct  1 11:45 BOOTX64.CSV
-rwxr-xr-x 1 root root 1196736 Oct  4 12:42 shimx64.efi
-rwxr-xr-x 1 root root 1153336 Oct  4 12:42 mmx64.efi
-rwxr-xr-x 1 root root 1133944 Oct  4 12:42 grubx64.efi
-rwxr-xr-x 1 root root     126 Oct  4 12:42 grub.cfg

Do you see anything weird? Should the ubuntu folder be there? What else can I look for? Boot-repair seems to fail to fix it, it also says it went successful, and I also still arrive to the boot console.

Thanks!

---

### Post by QIII on 2018-10-04
Moved to Ubuntu/Debian BASED.

---

