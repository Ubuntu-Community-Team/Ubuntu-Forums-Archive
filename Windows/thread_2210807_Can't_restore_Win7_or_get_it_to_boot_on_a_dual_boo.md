---
title: "Can't restore Win7 or get it to boot on a dual boot computer"
date: 2014-03-12
forum: Windows
---

### Post by jlh68 on 2014-03-12
I have a dual boot computer (Netbook 750) that has Ubuntu 12.04LTS and Win7 installed.  I can not get Win7 to boot, so I tried Boot-Repair-Disk and Win7 still does not boot. I have three windows partitions, sda1 is the restore partition, sda2 is the Win7 OS partition, and sda3 is the win boot loader partition. The rest of the partitions for my Linux system.  Grub has both sda1 and sda3 listed but they do not start win7 and if I just let it go I get a Win message that something is wrong with windows. (at least Microsoft admits it on screen :D) Windodw trys to fix itself withour sucess.  I have tried to use the restore win partition without sucess.

Basically I couldn't care less about having Windows on my computer, except I have a Logitec Harmony 650 TV Remote that has to be programed using a windows application, and I have a Tom-Tom GPS that has to be updated using windows (strange the LinuxOS on the Tom-Tom cannot communicate with a computer with Linux).  I have gotted the Harmony software to work completely in Linux using WINE, EXCEPT the computer and remote can not communicate, which might be a com port assignement. In any case my Harmony programing is saved on the Logitec internet site and will try to update the remote if it would connect.  That is another story.

So I would like to get my Windows to work again.  Any suggestions or point of attack to figure this out?

---

### Post by oldfred on 2014-03-12
Boot-Repair can only do minor fixes to Windows, you usually need a Windows repair flash drive or CD. If you can get into repair console make repair disk. Often chkdsk required after any Windows NTFS partition resize and that really should only be done with Windows disk tools and immediately reboot so it can run those fixes.
Grub can only boot a working Windows.

Sometimes installing the Windows boot loader to the MBR temporarily with Windows repair disk or Boot-Repair and booting with f8 may work also. 

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by newbie2244 on 2014-03-12
A little more info would be helpful. What were you doing when before this problem? Did you repartition your disk?  I have Ubuntu 12.04LTS and I had to go into BIOS to change boot order.

A little more info would be helpful.[br] What were you doing when before this problem? Did you repartition your disk?[/br] [br] I have Ubuntu 12.04LTS and I had to go into BIOS to change boot order to get both Ubuntu and Windows to boot.[/br]

---

### Post by jlh68 on 2014-03-13
Not sure what caused it, I have the same symptoms on two hard drives.  No new partitioning has been done. On the surface it seems like the Windows boot loader is not working correctly. I would have thought that the "restore" would restore both the WindowsOS and the Windows Boot Loader.  On one HD the boot of windows worked fine for awhile.  If fact I thought is was working, and then the other day I tried to boot Win7 and it would not go.

I remember in the ole days when windows came with some CD's to reinstall system, now it is on a 'hidden' partition (hidden to Windows not Linux) on the hard drive.  Of course my netbook does not have an optical drive.  

I looked at some of the sites you sent about making a repairUSB, that takes an optical drive which  my netbook does not have.

---

### Post by oldfred on 2014-03-13
This one  is USB.
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

Otherwise seems mostly a Windows issue. You may do better here.
       [http://www.sevenforums.com/](http://www.sevenforums.com/)
    
 [http://www.sevenforums.com/general-discussion/230019-repair-install-needed-but-no-discs.html](http://www.sevenforums.com/general-discussion/230019-repair-install-needed-but-no-discs.html)
[http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/](http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/)

---

