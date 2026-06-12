---
title: "Windows 8.1 cannot boot after installing Ubuntu 13.xx alongside Windows"
date: 2014-05-20
forum: Windows
---

### Post by Ville_Nilsson on 2014-05-20
First the Toshiba SATELLITE L650 - 11C that come preinstalled with Windows 7 then I got the cheap Windows 8 and then upgraded to Windows 8.1. And on my birthday I got money so I bought a new pc. So I wanted to test Ubuntu again on my laptop and then it didnt want to boot to Windows 8.1.
I have try Boot Repair but Windows still dosnt work.

PLEASE I NEED QUICK REPLY I AM GONNA SELL THE LAPTOP SOON AND I DON'T WAN'T TO BUY A NEW WINDOWS KEY FOR IT!!

---

### Post by oldfred on 2014-05-20
Post link to BootInfo report from Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did you make full backups of Windows before install of Ubuntu?

---

### Post by Ville_Nilsson on 2014-05-20
[http://paste.ubuntu.com/7493316/](http://paste.ubuntu.com/7493316/)

And no I didnt make any backup.

---

### Post by oldfred on 2014-05-20
Script cannot mount the sda2 partition. It is either hibernated or needs chkdsk. You can try installing the Windows boot loader to the MBR and directly boot Windows. 
It says sda1 is recovery, but it has boot flag? Windows systems usually have two recovery, one is the Windows Boot & repair partition and f8 gets you into repairs or it boots. 
But the vendor recovery restores system to like new and some systems just booting into that rewrites partition table and causes even larger issues. Did you always boot thru sda1. 

Boot-Repair cannot fix major Windows issues.
Did you leave Windows 8 in hibernated or fast boot? That always causes issues if dual booting.
And/or Windows needs chkdsk which you only can run from a Windows repair CD or flash drive.

This system is BIOS/MBR based, your newer one may be UEFI. Not sure which instructions then may be best to create a Windows repair flash drive. But you should be able to create a Windows repair flash drive from new system.

This is for  a Windows 8 UEFI repair flash, not sure if it works for BIOS also or not:
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

This is BIOS based on Windows 7 but should be the same for Windows 8.
      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[URL="http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html"]http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html

[/URL] WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 

[URL="http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html"]
[/URL]

---

### Post by Ville_Nilsson on 2014-05-20
I got a Windows 8 recovery disk and now?

---

### Post by oldfred on 2014-05-20
If install is not Windows 8, you cannot run any autofixes, but should be able to see if it can run chkdsk on the partition that is sda2. 

If it was just hibernation, you maybe should reinstall temporarily a Windows boot loader and see if you can either boot or use f8 to get into internal repair console.

If Windows 8 you can run auto repair.
[http://www.eightforums.com/tutorials/2843-automatic-repair-run-windows-8-a.html](http://www.eightforums.com/tutorials/2843-automatic-repair-run-windows-8-a.html)

For users that know Windows better.
       [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by Ville_Nilsson on 2014-05-21
Ok I think my Windows is working now but my dad told me to delite the partiton of Ubuntu so no when I boot my pc it says "BOOTMGR is missing Press Ctrl+Alt+Del to restart"

---

### Post by oldfred on 2014-05-21
Bootmgr missing is a Windows error.

Do you have boot flag on the partition with the Windows boot files. Usually in BIOS/MBR it is a separate 100MB (hidden) boot/recovery/repair partition. Unless you installed in just one NTFS which you can do if you only create one NTFS partition in advance.
Or if you installed in UEFI mode boot flag or active partition must be the efi partition.

 [http://www.eightforums.com/](http://www.eightforums.com/)


Always best to make sure Windows boots directly before deleting Ubuntu.

---

### Post by Ville_Nilsson on 2014-05-21
I have fix the bootmgr thing now but now it is booting from the old Windows 7 that only got the folders Windows, Programs, Progams (x86)?

---

### Post by oldfred on 2014-05-21
Moved to OtherOS since now just Windows.

---

### Post by Ville_Nilsson on 2014-05-21
What?

---

### Post by oldfred on 2014-05-21
This is an Ubuntu forum and you only are fixing Windows, so your thread was moved to the OtherOS where users with other systems can get help. 
But since your issues are Windows related you may do better in the Windows eight forum as it has those more knowledgeable with Windows.
My last Windows was XP and what little I know on newer ones it where those dual booting have made suggestions.

Windows only boots from one primary NTFS partition with the boot flag. Typically a second install moves its boot files into the first install and adds another entry into the BCD. So booting from the one install shows both Windows.

Discusses Vista, but applies to all BIOS/MBR based installs of Windows. 
 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

