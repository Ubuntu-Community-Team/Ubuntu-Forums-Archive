---
title: "vmdk file conversion"
date: 2010-12-05
forum: Virtualisation
---

### Post by rpscaringe on 2010-12-05
Is there a way to convert a vmdk file to the ovf format that virturalbox-ose uses for appliance inport/export?

---

### Post by CharlesA on 2010-12-05
Just add it as a new hard drive image.

If you only have the vmdk, that's all you can do.

---

### Post by rpscaringe on 2011-01-11
Charles,
Thanks for the info, it didn't work, but only because attempts to add the file as a new  hard drive image resulted in an eof error.  Apparently but not assuredly this has something to do with my external Toshiba TB drive, which fails to allow the entire 5.9 GB file to be copied even though there's plenty of space.  The work around was to copy the vmdk file over the network from my old linux box to the new one.
Now that I have the virtual machine transferred and running on VirtualBox 3.1.6_OSE,  I have a new problem...the --resize option for "VBoxManage modifyhd" is not recognized by version 3.1.6_OSE of the Command Line Interface.  Is there another way to increase the virtual disk space for the virtual machine?
Ray

---

### Post by CharlesA on 2011-01-11
It sounds like the external hard drive is formatted as FAT32. If it was NTFS or one of the Linux file systems it would be fine. :)

As for the resizing thing, I'm not sure, I've never tried to resize a Virtual disk.

---

### Post by rpscaringe on 2011-01-11
check, the sys monitor lists type as "vfat", it was definitely set up for windows...I'll look into reformatting.
I'll post the vdisk expansion as a separate question...

---

