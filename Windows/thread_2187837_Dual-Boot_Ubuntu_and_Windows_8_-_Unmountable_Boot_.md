---
title: "Dual-Boot Ubuntu and Windows 8 - Unmountable Boot Disk (Windows)"
date: 2013-11-14
forum: Windows
---

### Post by man.person on 2013-11-14
[COLOR=#000000][FONT=Arial]I was working with a CAD program in Windows 8, and when I went to save a file, the computer locked up. After a while, I rebooted the computer, only to find that Windows no longer boots.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have a dual-boot system between Windows 8 and Ubuntu 13.10, both on the same HDD. I can access Ubuntu easily, but most of the Windows files are write protected due to the presence of hiberfil.sys (even though I disabled hibernation a few days ago).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
I have tried the following: 

-Normal boot
-Recovery boot
-BIOS secure boot
-Recovery media boot
-Asking nicely
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am pretty confident that this is a hard drive error, but I cannot boot to CMD to run CHKDSK.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Detailed error description: The machine boots to either the GRUB menu or the VAIO system setup menu, depending on which boot mode I'm in. After selecting a boot option, it proceeds to a black splash screen with "VAIO" across the screen. Every other normal boot, the text "Preparing for auto-repair" appears. Then, the screen goes black, and a Blue Screen pops up with the mentioned error after a seemingly random (sometimes very long) time interval.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Computer specs: Win8/Ubuntu13.10 x86-64 with Intel i9 2.4GHz processor, 8GB ram, iTB HDD, 24GB SSD, Sony VAIO SVT15115CXS.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]

Specifically, I'm looking for a way to run CHKDSK, or mark that it should be run on startup, through Ubuntu. I think this may fix my problem, but I don't know where to start...[/FONT][/COLOR]

---

### Post by oldfred on 2013-11-14
You cannot run chkdsk from Ubuntu. That can only be run from Windows or a Windows repairCD or Flash drive. 

If hiberfile flag is set I do not think the Linux NTFS file check ntfsfix will run, but it does set chkdsk flag as it can only make minor repairs itself.

       man ntfsfix
Change to your partition, sda1 is just example
sudo ntfsfix /dev/sda1

      Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by man.person on 2013-11-15
Hey, thanks for the reply. I ran ntfsfix on the affected partitions with no effect. Since then, however, my HDD has completely stopped working. It started making the same clicking sound that it makes with a hard shutdown, and nothing is recognizing the HDD as existing anymore. I can boot Ubuntu from a USB live install, but other than that, the computer can't locate either of the two operating systems.

---

### Post by oldfred on 2013-11-15
Sounds like total hard drive failure.
Clicking noises are almost always a bad sign.
Does BIOS show drive? If BIOS does not show drive nothing will mount or even see it.
If you  can see drive then take a look with disks or disks utility and click on drive and see what Smart Data shows.

---

