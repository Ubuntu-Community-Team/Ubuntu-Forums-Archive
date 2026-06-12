---
title: "Uefi BIOS doesn't recognize Hard Disk after erasing Windows 8.1 through ElementaryOS"
date: 2014-11-30
forum: Ubuntu/Debian BASED
---

### Post by ogromad on 2014-11-30
My Notebook Asus X552c Specs:


-CPU: Intel Core I7-3537U, 2.0 GHz
-RAM: 4 GB
-Hard Disk: HGST HTS545050A7E680 (500 GB or 500.107 MB)
-CDROM: MATSHITADVD-RAM UJ8C2 S


I was tired of using Windows 8.1 on my notebook because of some problems with applications 
compatibility.


So i took ElementaryOS,disabled Secure Boot and enabled CSM into "Uefi Aptio Setup Utility" BIOS,and started the OS installation.
When i got into the "installation type" part,i've chosen "something else" option and deleted 
every default partition of the hard drive ("Windows boot manager" included).
I've divided the hard drive in 3 partitions:
-490 GB for Elementary OS;
-9108 MB for a Swap partition;
-999 MB for the BIOS;
after completing the installation process and rebooting the notebook,i was not able to access 
ElementaryOS because of the "Reboot and select proper boot device" screen.
So i checked the boot options into the BIOS and the only one Available is the CDROM (even if 
the "Sata Configuration" under "Advanced" Tab recognizes the Hard Disk).

Is there a way to fix this problem?


Thanks!

---

