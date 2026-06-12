---
title: "After reinstalling Ubuntu 18.04 - Windows 7 doesn't boot anymore..."
date: 2020-04-14
forum: Windows
---

### Post by rory4ever on 2020-04-14
So my set up was as follows: 

1x 120GB HDD - Ubuntu 18.04.3 install.
1x 240GB HDD - Windows 7 install

It worked fine, not by using the GRUB menu but via F12 and then I could select the Windows 7 bootloader. 

However, due to some broken packages and all I needed to reinstall Ubuntu. The only thing I did was, using the live USB of Ubuntu, deleting the Ubuntu partition (I never touched my 2nd HDD btw) and made a fresh install of Ubuntu 18.04.4
After that, Ubuntu booted without any problem, but Windows 7 was gone. 
It isn't shown in GRUB menu, and neither using the F12 boot menu. On the latter I could select the 2nd HDD (240GB) with Windows 7 installed on it but it just ignores it and it boots in ubuntu instead. 
sudo os-prober couldn't find a Windows installation. 

Windows is installed on SDA (SDA1 for an unknown windows partition, and SDA2 for the system partition (?))

I tried boot-repair (recommended option selected) but to no avail. I have the pastebin of it here: [http://paste.ubuntu.com/p/GV68bgttW5/](http://paste.ubuntu.com/p/GV68bgttW5/)

I'm not an expert at all but it looks like the boot partition for Windows 7 is broken or something? or the boot flag isn't set correctly?

Any help much appreciated, thanks!

---

### Post by yancek on 2020-04-14
> However, due to some broken packages and all I needed to reinstall Ubuntu 

Probably not, if you had posted the problem here someone might have had a solution or at least a suggestion to try to repair the problem.  It's not necessary to re-install the system on every problem as with windows.

If you have a windows OS on one physical hard drive and want to install Ubuntu (or any Linux) on a separate hard drive, it is best to physically dis-connect the windows drive before beginning the Ubuntu install.  If you can't, then see if it is possible to disable it in the BIOS.

It's difficult to tell what happened and for some reason, your boot repair output does not show all the usual information.  The unknown partition you refer to shows on line 33 as sda1, Microsoft Reserved Partition.  A standard factory install of windows 7 would generally show that as a separate boot partition and sda2 would be the OS.  Often, there would be a reserve or other partiiton.

Scroll down to line 353 and your will see below.  128M is a standard size for a windows 7 boot partition so that may be it. 

> /dev/sda1    2048    264191    262144   128M Microsoft reserved

Beginning at line 490 you would ordinarily see the windows boot files on that partition but for some reason they don't show.  Not there?
Line 349 shows the windows disk as gpt.  Windows installed on a GPT drive is required to be installed in UEFI mode and it is not.  Don't know how you did that.  Did you change the drive to GPT or did you have an UEFI install of windows and have overwritten the EFI partition?  Might be what sda1 was?

Line 361 shows the other disk as dos which is a legacy install.  A legacy install of Ubuntu Grub will boot a legacy install of windows and will not boot an EFI install of windows.

Lines 424/425 indicate that sda2 and the bootmgr file may need repair.  Can't do that from Ubuntu.  You need a windows install or repair CD/DVD or similar software.

Do you know how to mount partitions?  If so, boot the Ubuntu install usb and mount sda1 and check to see what files are there.  You should see several windows boot files.  If you don't know what to expect, post here and someone should be able to tell you.  While you are booted into Ubuntu on the USB, again open a terminal and run:  sudo gparted to open GParted and select the sda drive in the upper right and in the main window, highlight sda1 then right click it and select Manage Flags and then click the check box to the left of boot to mark that as the boot/active partition.  THis is required on windows systems and meaningless on Linux.  Don't know if this will help but it isn't going to create a problem.

---

### Post by rory4ever on 2020-04-27
> **yancek said:**
> Probably not, if you had posted the problem here someone might have had a solution or at least a suggestion to try to repair the problem.  It's not necessary to re-install the system on every problem as with windows.

If you have a windows OS on one physical hard drive and want to install Ubuntu (or any Linux) on a separate hard drive, it is best to physically dis-connect the windows drive before beginning the Ubuntu install.  If you can't, then see if it is possible to disable it in the BIOS.

It's difficult to tell what happened and for some reason, your boot repair output does not show all the usual information.  The unknown partition you refer to shows on line 33 as sda1, Microsoft Reserved Partition.  A standard factory install of windows 7 would generally show that as a separate boot partition and sda2 would be the OS.  Often, there would be a reserve or other partiiton.

Scroll down to line 353 and your will see below.  128M is a standard size for a windows 7 boot partition so that may be it. 



Beginning at line 490 you would ordinarily see the windows boot files on that partition but for some reason they don't show.  Not there?
Line 349 shows the windows disk as gpt.  Windows installed on a GPT drive is required to be installed in UEFI mode and it is not.  Don't know how you did that.  Did you change the drive to GPT or did you have an UEFI install of windows and have overwritten the EFI partition?  Might be what sda1 was?

Line 361 shows the other disk as dos which is a legacy install.  A legacy install of Ubuntu Grub will boot a legacy install of windows and will not boot an EFI install of windows.

Lines 424/425 indicate that sda2 and the bootmgr file may need repair.  Can't do that from Ubuntu.  You need a windows install or repair CD/DVD or similar software.

Do you know how to mount partitions?  If so, boot the Ubuntu install usb and mount sda1 and check to see what files are there.  You should see several windows boot files.  If you don't know what to expect, post here and someone should be able to tell you.  While you are booted into Ubuntu on the USB, again open a terminal and run:  sudo gparted to open GParted and select the sda drive in the upper right and in the main window, highlight sda1 then right click it and select Manage Flags and then click the check box to the left of boot to mark that as the boot/active partition.  THis is required on windows systems and meaningless on Linux.  Don't know if this will help but it isn't going to create a problem.


Thanks and sorry for the delayed response, I had some personal issues...

So, I reinstalled Ubuntu but chose legacy instead of EFI while my Windows installation was already installed as EFI... this broke the windows boot. I did not change the drive to GPT, I guess i have overwritten the EFI partition, probably using some settings with boot-repair earlier, and tried to install grub on that partition which further broke stuff...(filesystem was overwritten)  However, I always booted windows using the windows boot manager (F12, select the harddrive where windows installation resides on) and that worked great, I never used the grub menu to select windows so I guess a legacy install of ubuntu grub doesn't affect this since I don't use the menu to boot windows (?) 

I did repair the bootmgr file using a windows install usb but that didn't work. 

I mounted sda1, it states that 12MB is used but the file manager isn't showing any files at all (also checked show hidden files)

---

### Post by yancek on 2020-04-27
> I did repair the bootmgr file using a windows install usb but that didn't work.  

Sorry, can't help with that.  All I can tell you for certain is that you won't fix your windows from Ubuntu or any Linux due to the extreme proprietary nature of the software (not as proprietary as Apple but ...?)

If you're not really familiar with bootloaders and want both a windows and Linux system installed, the absolute simplest and safest way to do this is to physically dis-connect one drive while you are installing an OS on the other drive.  This is problematic on laptops but you may be able to disable the drive in the BIOS.

Also, you can install windows EFI and Ubuntu Legacy or the reverse and boot without problem if they are on separate drives.  Just access the BIOS the way you have been.  The disadvantage is basically that it takes a few seconds longer to do this to boot because a Legacy Grub will not boot a UEFI window and an EFI install of Grub will not boot a Legacy install of windows.  Windows won't boot Grub either way, well it will do a legacy boot if both systems are legacy but it's a pretty convoluted process.

Do you know how to use a terminal to create a mount point and mount a partition (the EFI on sda1)?  If so, can you post that or if you have made some changes, try running the Create BootInfo Summary option from boot repair and posting the link.

---

### Post by rory4ever on 2020-04-28
> **yancek said:**
> Sorry, can't help with that.  All I can tell you for certain is that you won't fix your windows from Ubuntu or any Linux due to the extreme proprietary nature of the software (not as proprietary as Apple but ...?)

If you're not really familiar with bootloaders and want both a windows and Linux system installed, the absolute simplest and safest way to do this is to physically dis-connect one drive while you are installing an OS on the other drive.  This is problematic on laptops but you may be able to disable the drive in the BIOS.

Also, you can install windows EFI and Ubuntu Legacy or the reverse and boot without problem if they are on separate drives.  Just access the BIOS the way you have been.  The disadvantage is basically that it takes a few seconds longer to do this to boot because a Legacy Grub will not boot a UEFI window and an EFI install of Grub will not boot a Legacy install of windows.  Windows won't boot Grub either way, well it will do a legacy boot if both systems are legacy but it's a pretty convoluted process.

Do you know how to use a terminal to create a mount point and mount a partition (the EFI on sda1)?  If so, can you post that or if you have made some changes, try running the Create BootInfo Summary option from boot repair and posting the link.

I'm aware you can't help with windows stuff. Yes, I used the bios boot to switch between Windows and Ubuntu and it worked fine that way for a year or so, until the Ubuntu re-install. 

I know how to use a terminal to create a mount point and mount a partition. i just did and that went fine but although Gparted states that SDA1 (the 128MB NTFS partition) has about 12MB of data on it I couldn't find a single file on it (also checked hidden files)

I created a new pastebin for the bootinfo summary. One thing that has changed is because I formatted SDA1 as NTFS, that boot-repair is now able to determine that it is a valid Windows partition.
However, I still see that the boot files are not there but on SDA2 they are there. I think maybe they should be on SDA1 and somehow Windows only checks SDA1 for the boot process? 

[http://paste.ubuntu.com/p/mQVzxVmSVj/](http://paste.ubuntu.com/p/mQVzxVmSVj/)

---

### Post by yancek on 2020-04-28
On your current boot repair, line 58 shows /dev/sda1 as an EFI partition but if you look above, as you indicate in your post, there are no files shown.  Line 48 of boot repair shows the disklabel type as gpt which requires a UEFI install for a windows system.  You should have  at least  Boot and Microsoft folders there (sda1) for windows with different files used to boot windows in UEFI mode.  There would also be different boot files on the windows system partition which is sda2. Since you have a GPT drive with windows, you must have an EFI install of windows and the EFI partition (sda1 in your case) needs to be formatted vfat (FAT32).  You will need to find out how these files can be replaced and how you can re-install the windows EFI boot files.  The only step I can tell you is that you need to first format sda1 as vfat.  Good Luck.

---

### Post by rory4ever on 2020-04-28
> **yancek said:**
> On your current boot repair, line 58 shows /dev/sda1 as an EFI partition but if you look above, as you indicate in your post, there are no files shown.  Line 48 of boot repair shows the disklabel type as gpt which requires a UEFI install for a windows system.  You should have  at least  Boot and Microsoft folders there (sda1) for windows with different files used to boot windows in UEFI mode.  There would also be different boot files on the windows system partition which is sda2. Since you have a GPT drive with windows, you must have an EFI install of windows and the EFI partition (sda1 in your case) needs to be formatted vfat (FAT32).  You will need to find out how these files can be replaced and how you can re-install the windows EFI boot files.  The only step I can tell you is that you need to first format sda1 as vfat.  Good Luck.

You helped me with that single step :) 

Apparently, after all the hassle, the very last step I needed to take was to make sure the Win7  installation USB, created with Rufus, needed to be GPT (EFI), and it was  MBR before, hence the weird stuff going on. 

So in short, the solution was to delete all partitions except the  data(windows+programs) partition, create 1 new EFI partition of 100mb  (formatted as FAT32), 1 recovery partition of 128MB and copy the  bootfiles using bootsect.exe (part of the Windows 7 rescue environment boot USB) to the EFI boot partition. After that it still  didn't work but after creating the correct Windows 7 repair USB, the  repair utility already stated that there were some errors with my  Windows 7 installation when it was scanning for Windows installations. I  clicked on "repair" and after that my problem was solved. Thanks  everyone for the help!

---

### Post by yancek on 2020-04-28
Glad you got it working.

---

