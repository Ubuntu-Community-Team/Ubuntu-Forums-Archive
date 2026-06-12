---
title: "cannot install windows with woeusb"
date: 2018-11-21
forum: Windows
---

### Post by skyn4 on 2018-11-21
I'm trying to install windows 7 to an external hdd but it says its too big

Installation failed!
Exit code: 256
Log:
WoeUSB v@@WOEUSB_VERSION@@
==============================
Mounting source filesystem...
Wiping all existing partition table and filesystem signatures in /dev/sde...
/dev/sde: 8 bytes were erased at offset 0x00000200 (gpt): 45 46 49 20 50 41 52 54
/dev/sde: 8 bytes were erased at offset 0x2baa1475e00 (gpt): 45 46 49 20 50 41 52 54
/dev/sde: 2 bytes were erased at offset 0x000001fe (PMBR): 55 aa
/dev/sde: calling ioctl to re-read partition table: Success
Ensure that /dev/sde is really wiped...
Creating new partition table on /dev/sde...
Creating target partition...
Error: partition length of 5860524976 sectors exceeds the msdos-partition-table-imposed maximum of 4294967295
The command "parted --script "${target_device}" mkpart primary "${parted_mkpart_fs_type}" 4MiB -- -1s" failed with exit status "1", program is prematurely aborted
Unmounting and removing "/media/woeusb_source_1542804885_21021"...
You may now safely detach the target device

---

### Post by yancek on 2018-11-22
How big is the drive you are trying to install to?  If over 2TB, you might have the problem of the 2TB limit discussed at the link below.  

[https://administratosphere.wordpress.com/2011/03/29/dos-partitions-fdisk-and-the-2tb-limit/](https://administratosphere.wordpress.com/2011/03/29/dos-partitions-fdisk-and-the-2tb-limit/)

This isn't an external usb drive is it?

---

