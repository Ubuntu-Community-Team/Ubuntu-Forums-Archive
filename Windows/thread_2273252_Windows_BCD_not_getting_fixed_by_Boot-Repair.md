---
title: "Windows BCD not getting fixed by Boot-Repair"
date: 2015-04-11
forum: Windows
---

### Post by Carteazzy on 2015-04-11
Hello everyone, 
I have been booting into Grub recently when I start my computer, however I decided to return back to MBR for awhile. To do that, I used a program on Windows but something went wrong, and now when I try to boot into my windows partition I get the error 
> **[SIZE=2]File:\Boot\BCD. Status:0xc0000098. Info:The Windows Boot Configuration file does not contain a valid OS entry.[/SIZE]**



The advised recovery method is to run the command prompt from windows advanced boot recovery, but my HP support assistant doesn't allow the command prompt to be accessed.

I decided to try to fix this through Ubuntu instead, so after running Boot-Repair my result is [http://paste.ubuntu.com/10802517/](http://paste.ubuntu.com/10802517/) which says that all of my boot directories are fine. I now have no idea where to go, nothing appears to work. Any help would be greatly appreciated.

---

### Post by Carteazzy on 2015-04-11
Hello everyone, 
I have been booting into Grub recently when I start my computer, however I decided to return back to MBR for awhile. To do that, I used a program on Windows but something went wrong, and now when I try to boot into my windows partition I get the error 
> **[SIZE=2]File:\Boot\BCD. Status:0xc0000098. Info:The Windows Boot Configuration file does not contain a valid OS entry.[/SIZE]**



The advised recovery method is to run the command prompt from windows advanced boot recovery, but my HP support assistant doesn't allow the command prompt to be accessed.

I decided to try to fix this through Ubuntu instead, so after running Boot-Repair my result is [http://paste.ubuntu.com/10802517/](http://paste.ubuntu.com/10802517/) which says that all of my boot directories are fine. I now have no idea where to go, nothing appears to work. Any help would be greatly appreciated.

---

### Post by oldfred on 2015-04-11
Moved to Windows sub forum. Also duplicated merged.

From Linux you can only fix a few Windows issues. 
Best to have a Windows repairCD or flash drive.

To repair BCD or run chkdsk you must have Windows repair tools and you also have somehow converted your sdb drive to dynamic partitions, shown as SFS in Linux. That does not work with Linux nor even some Windows repair tools. Since only one partition best to undo it. But Windows does not have an undo, you have to use third party tools.

If you did not create a Windows repair disk to make repairs, you may be able to use Boot-Repair's advanced mode to install a Windows boot loader, then booting Windows use f8 to get into its own repair console.

       f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
Restore MBR for win7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Repair BCD - not recommended for dual booting, just Windows repairs
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)


 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Then once you get Windows working you can use Boot-Repair or your Linux live installer to restore grub to MBR. Grub really only boots working Windows.
      
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by Carteazzy on 2015-04-11
Thanks for the in-depth response. When I choose to boot into safe mode with command prompt it instead just brings me to some HP-recovery assistant, blocking me from the prompt. The reson I began all of this was to install my Windows on my SSD (the 120gb drive), so after I migrate Windows do you advise that I just erase all of the partitions on that drive?

---

