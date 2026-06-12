---
title: "Problem in Windows Boot Manager/UEFI in dual boot"
date: 2018-08-18
forum: Windows
---

### Post by nitishbahl24 on 2018-08-18
[COLOR=#242729][FONT=Arial]PC model- Lenovo Ideapad 300 
OS- Windows 10 dual booted with Ubuntu 18.04[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I am not able to start windows or view grub menu or see Lenovo logo(which was visible earlier) after one fine day I put my Windows to sleep. Sleep mode was working perfectly fine earlier. Now only Ubuntu 18.04 is starting and grub menu is not visible, also windows is not able to start properly. The display is black until Ubuntu loads. How can I recover windows and bios. When grub is updated in terminal it successfully detects all OS.
I have tried BOOT-REPAIR tool in ubuntu to reinstall grub and change several settings several times but of no use. The most recent boot info summary is - [http://paste.ubuntu.com/p/32WmszmhWj/](http://paste.ubuntu.com/p/32WmszmhWj/)

Please help[/FONT][/COLOR]

---

### Post by yancek on 2018-08-18
Two things that are obvious problems are the fact that you have 2 EFI partitions on the same drive.  That is never necessary and is a bad thing so either format or delete sda8 as sda1 is your original EFI partition and has the correct EFI files for both windows and Ubuntu and your windows menuentry in grub.cfg is pointing to the sda1 EFI files.  The EFI partition should be marked active/bootable for windows and you should be able to do that from GParted in Ubuntu.  Not knowing what boot options you have, it's difficult to give more specifics.  Some systems will allow you to select and option to boot from EFI file in the BIOS.  If you can do that, make the selection listed in boot repair to select grubx64.efi

---

### Post by nitishbahl24 on 2018-08-18
For troubleshooting I tried to boot to windows recovery i.e sda6 from ubuntu but things got worse as due to no display I cannot enter/boot ubuntu now.
I am using Lenovo Ideapad 300 and it is showing black/dim screen now. Another issue is that no Lenovo logo is coming which used to come before. I tried resetting the device but no display is coming.

---

### Post by oldfred on 2018-08-18
It looks like sda8 is a Lenovo FAT32  for its own repair/recovery boot.
As long as it does not have boot flag making it the current working ESP, it is ok. Somehow Lenovo must move boot flag or is able to use it as ESP when booting its own repair/recovery boot files.

Windows recovery may erase drive and restore Windows or just refresh Windows. Each vendor does that differently. Generally better to make a full backup of your Windows after you have removed all the cruft and reconfigured the way you want it.

Post a new link to summary report.

You also may need to house clean all the old Boot-Repair logs in your ESP, so show 11 folders.

---

### Post by westie457 on 2018-08-20
Try booting using the 'Novo' button to get a different boot menu.
The 'System Recovery' option will not work. That was disabled when you changed the size of a partition. There several reports on the Lenovo Forums about the 'One-key Recovery' not working.
All other options in the novo button boot menu should work.

---

