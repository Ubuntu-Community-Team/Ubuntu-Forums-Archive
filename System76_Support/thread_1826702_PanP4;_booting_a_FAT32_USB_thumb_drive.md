---
title: "PanP4; booting a FAT32 USB thumb drive"
date: 2011-08-16
forum: System76 Support
---

### Post by robtg on 2011-08-16
I've got a PanP4 with the BIOS that was shipped with it (1.02.22S76).   When creating a bootable USB drive, I've found that the PanP4 will not boot from a USB thumb drive formatted as FAT32 but will boot from one formatted as FAT.  This limits my bootable USB thumb drive to an old 1GB model and precludes me from installing a distro from a DVD ISO image.  Is this limitation a function of the BIOS?  The software that I'm using to create the bootable USB thumb drive (Universal USB Installer from pendrivelinux.com) proposes to format the thumb drive as FAT32 (I don't let the software format the thumb drive) so I'm thinking that this must work on some machines.  Windows won't format a USB drive larger than 1GB as FAT (insists on FAT32) so when this poor old USB drive bites the dust I'm out of luck.

Just curious.  Thanks.

Rob

---

### Post by Furball588 on 2011-08-17
Doesn't make a lot of sense.  The only thing that the bios is going to look for is a boot sector.  

How big is your image file and how big is your thumb drive?  I do remember there were some limits as to what you could do with fat32/

---

### Post by robtg on 2011-08-17
The USB drive that works is 1GB; the one that doesn't work is 8GB.  The image file that I tried to use was about 1.1GB; the Universal USB Installer program reads the ISO image and copies the files contained in it to the USB drive while also creating a boot sector.   A CD-sized ISO image also will not work on the 8GB USB drive (formatted as FAT32) but works on the smaller 1GB drive (formatted as FAT).

Rob

---

