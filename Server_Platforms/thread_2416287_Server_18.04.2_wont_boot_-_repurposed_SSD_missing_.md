---
title: "Server 18.04.2 wont boot - repurposed SSD missing EFI partition"
date: 2019-04-08
forum: Server Platforms
---

### Post by aljames2 on 2019-04-08
Alternate download.  Clean install using USB  cdimage ISO.  The SSD drive had been previously used as Windows 10 operating system in another machine.  I used Windows to delete partitions and format FAT32.  This will be a Ubuntu only system, no dual boot.

Ubuntu install seemed to go well until near the end a message popped up warning me that the EFI partition was missing and to go back and create it or the system might not boot.  I proceeded on figuring the system would create it after the first reboot.  At reboot I get a message that the drive is not bootable.  I guess I should have listened, :)

In BIOS I have Boot Mode set to UEFI only, and I have USB Legacy Support enabled?

I want to start over but need advice on how to properly prepare the drive?

---

### Post by darkod on 2019-04-08
What exactly did you format as FAT32? The whole SSD?

---

### Post by aljames2 on 2019-04-08
I used the disk manager in Windows 10 and deleted all the partitions and did a complete reformat (FAT32), to clear the disc for use in my server box.  I figured Ubuntu would just reformat it to the new partition structure & file system.

---

### Post by oldfred on 2019-04-08
Ubuntu will not install to FAT32, but if UEFI you will need an ESP - efi system partition which is UEFI. That can be anywhere from 100MB to 600MB, formatted FAT32 with boot flag or esp flag if using parted/gparted from live installer. Code ef00 if using gdisk.

       [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by aljames2 on 2019-04-08
Correction I think it was formatted NTFS, the Windows default format setting.

I’ll start over and get the EFI partition set first, then install.  Thanks!

---

### Post by darkod on 2019-04-09
Create the EFI partition (as mentioned it should be FAT32) and leave the rest of the disk unpartitioned. So, no partitions at all.

The installer will take care of the rest.

---

### Post by aljames2 on 2019-04-09
Excellent, got it right now.  Server installed & booting correctly.  I got the EFI partition set with Gparted, then ran the installer and set up my /boot partition & all the LVM partitions.
Thanks again :)

---

