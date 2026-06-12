---
title: "save Grub on 2nd disk install of daily build"
date: 2017-07-16
forum: Ubuntu Development Version
---

### Post by jloveless on 2017-07-16
I have an SSD (sda) with Grub as the boot loader. Ubuntu Gnome 17.04 is also on the SSD.
 I have Win10 on a 25% partition of a 1TB drive (sdb1). I want to be able to install an occasional 17.10 daily build on the large remaining partition sdb3-formatted as ext4.  My grub on sda is customized and I don't want to lose it during installation of 17.10. The Ubuntu install wants to overwrite it making the 17.10 the primary boot target.  Can anyone give me advice for telling the 17.10 install process to disregard grub - I will set it up manually with Grub Customizer later. Or is there another solution?

---

### Post by oldfred on 2017-07-16
UEFI or BIOS?
If UEFI be sure to backup the ESP before installing another copy of Ubuntu. Second copy will overwrite and make second copy primary boot.

I prefer to manually customize 40_custom and back that up.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 

      
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

