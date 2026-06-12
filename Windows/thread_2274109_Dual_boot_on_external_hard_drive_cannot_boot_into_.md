---
title: "Dual boot on external hard drive cannot boot into Windows7"
date: 2015-04-17
forum: Windows
---

### Post by julienbg18 on 2015-04-17
Hello,

I have recently installed Ubuntu on my external hard drive with Windows7 already preinstalled on my internal hard drive. I can easily boot on my external hard drive and run Ubuntu, but I am now unable to boot into windows7 from my internal drive or the GRUB menu when booting from my external hard drive. When trying to boot into Windows7, I always get the error message that "Windows failed to start. A recent hardware or software change might have caused the issue after you install Windows Updates". 

I have looked around for solutions and found boot-repair, but I don't want to run the recommended repairs before understanding what is really happening and if indeed the repairs will fix my problem. So, I have run boot info and here is the result: [http://paste.ubuntu.com/10841274/](http://paste.ubuntu.com/10841274/) 

Can anyone help me?

Thank you very much for your help!

---

### Post by yancek on 2015-04-17
You had windows installed in UEFI mode and installed Ubuntu in MBR mode which conflict.  They both need to be UEFI or they both need to be MBR.  I don't use UEFI myself so won't suggest you invoke the changes suggested in the boot repair script.  You will probably have to reinstall Ubuntu in UEFI mode but there may be some other method to make this change.  Best wait for someone with a little more experience in the area.

---

### Post by oldfred on 2015-04-17
You can dual boot with one UEFI and the other BIOS based, but it can be a hassle. Some systems require you to go into UEFI and turn on/off UEFI or BIOS/CSM to match system you are booting. Others may let you use one time boot key often f10 or f12.

Only if you want external drive to boot on an older system without UEFI would I suggest keeping it BIOS, better to have all systems the same and since Windows is UEFI then Ubuntu should be UEFI.

Also even if you want BIOS on external drive better to have both the efi partition and a bios_grub partition using gpt partitioning not the very old MBR(msdos). Then later you could convert drive to UEFI. Windows only boots from gpt with UEFI but as an external drive it will be only Ubuntu or data partitions. Windows can easily read NTFS data partitions on a gpt partitioned drive.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

Also back up entire efi partition as welll as Windows. I installed to sdb in UEFI mode a second Ubuntu install and it overwrote my efi partition on sda. With Windows it will not overwrite it, but add an ubuntu folder on sda. But you will want to configure the external as UEFI bootable also. And that is different than an internal drive as USB must boot from /EFI/Boot folder using bootx64.efi which we make by renaming grub or shim. 
Not as straight forward with UEFI as it was with BIOS.

For any second drive be sure to only use Something Else install option. 

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by julienbg18 on 2015-04-18
Thanks a lot for the advice! But just to be sure, would you recommend the boot-repair recommended repairs? It seems it wants to reinstall GRUB in uefi.

And does the conflict explain why I am unable to boot into windows7 even if I disable or enable UEFI in my BIOS. I would really like to get access back to windows7.

---

### Post by oldfred on 2015-04-18
If your Windows is UEFI, then you should only have to go into UEFI boot menu and choose Windows. With UEFI all boot loaders co-exist in the efi partition.

I would run the Boot-Repair fix, but grub will probably install to efi partition on sda.

---

### Post by julienbg18 on 2015-04-18
Thats the thing I am unable to boot windows7 even when in UEFI. One thing I should point out is that I previously had a dual boot with windows8 but eventually deleted it. At the time, I had used EasyBCD to delete the windows8 boot option from windows boot manager. I thought it would delete it, but is it possible that the UEFI boot is actually a left over from Windows8 and doesn't belong to Windows7. It could certainly explain why I can't boot Win7 in UEFI.

---

### Post by oldfred on 2015-04-19
Were you able to boot both Windows from the one Windows that booted? The BCD would list both.
But if one was UEFI and one BIOS that normally will not work if on same drive.
Windows only boots from gpt partitioned drives with UEFI.
And Windows only boots from MBR(msdos) partitioned drives with BIOS.
If you overinstall with different boot mode, it converts partitioning and then other system is unusable. All systems must be in same boot mode, especially with Windows.

Since drive is gpt & you have the Microsoft reserved partition just before the first NTFS partition, then it just about has to be UEFI. And then you need to run Windows repairs to fix it. It is pretty much the same repair commands, but you must be in UEFI mode. Best to use a Windows 7 UEFI repair flash drive. But most Windows 7 installers were BIOS by default and had to be converted to be UEFI. I think it was just create an efi folder and move some files so it was UEFI bootable.

---

### Post by julienbg18 on 2015-04-19
So what exactly would you suggest I do to solve my problem?

Thanks a lot for the help.

---

### Post by oldfred on 2015-04-19
I do not know Windows repairs with UEFI. 
EVen though Windows 7, you probably need to follow the Windows 8 instructions as they usually are UEFI, and Windows 7 is usually BIOS. 

 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

You may be able to restore a BCD with EasyBCD, but normally with UEFI you do not want to use EasyBCD as a boot manager.

      
 Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

Do you have an UEFI bootable Windows 7 repair flash drive?

---

### Post by julienbg18 on 2015-04-19
No I don't. But I could boot a windows7 installation disc in UEFI.

---

### Post by oldfred on 2015-04-19
Boot-Repair and Linux can only do minor fixes to Windows. You really need a Windows repairCD or flash drive.
Do you know someone else with Windows 7 64 bit? School, work, friend. Take your flash drive to them and create a Windows repair flash drive and convert it to UEFI boot.

Much better to make this when Windows is still working. My new Windows 8 system wanted an 8GB flash drive for the Windows startup recovery/repair disk.
       Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

[http://www.eightforums.com/tutorials/13326-downgrade-windows-8-windows-7-a.html](http://www.eightforums.com/tutorials/13326-downgrade-windows-8-windows-7-a.html)

  Convert Windows 7, 8 or 8.1  BIOS to UEFI - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

---

### Post by julienbg18 on 2015-04-20
I have tried the boot repair fix and I am now booting Ubuntu in UEFI, but I am still unable to boot into windows7. Here is the link for the boot repair : [http://paste.ubuntu.com/10854712/](http://paste.ubuntu.com/10854712/)

---

### Post by oldfred on 2015-04-20
Can you directly boot Windows from UEFI menu, or get into the internal repair console?

Boot0000* Windows Boot Manager    HD(1,800,64000,33f55c50-d46e-46cf-9db8-e99a5189e284)File(EFIMicrosoftBootbootmgfw.efi)

That is not from grub menu.

---

### Post by julienbg18 on 2015-04-20
How can I do that? Aside from the windows options in GRUB that doesn't work, I have an entry in my BIOS for Windows Boot Manager that doesn't work either.

When I select Windows Boot Manager in my Bios, I get error :  

Status : 0xc0000225  
Info: A required device isn't connected or can't be accessed.

And I got 3 entries in  my GRUB menu : Windows UEFI bootmgfw.efi,  Windows Boot UEFI loader and Windows Boot Manager(on /dev/sda1)
They all give me the same error when I select them : 

file : \windows\system32\winload.efi
status : 0xc0000001 
info : The application or operating system couldn't be loaded because a required file is missing or contains errors.


And also, what is the difference between a repairCD and running the repair tool on a windows7 installation disk? Surely looks like the same menu from the pictures I have seen.

---

### Post by oldfred on 2015-04-20
If your install disk includes the recovery console then it is the same thing.
Just be sure to boot in UEFI mode to make repairs.

---

### Post by julienbg18 on 2015-04-20
I booted in UEFI, but the statup repair failed in [COLOR=#333333][FONT=Segoe UI][SIZE=2]System files integrity check[/SIZE] [SIZE=2]and repair[/SIZE]  [SIZE=2]with failed-error code 0x490.[/SIZE][/FONT][/COLOR]

---

### Post by oldfred on 2015-04-20
No idea what Windows codes are. Best to try the Windows forums.

Moved to Windows sub-forum since Windows issues.

---

### Post by julienbg18 on 2015-04-20
Alright, thanks a lot for the help!

---

### Post by oldfred on 2015-04-20
I guess I posted some Windows repair links different in this thread. 
And they said this worked for them.
[http://ubuntuforums.org/showthread.php?t=2273360&p=13268865#post13268865](http://ubuntuforums.org/showthread.php?t=2273360&p=13268865#post13268865)
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

---

