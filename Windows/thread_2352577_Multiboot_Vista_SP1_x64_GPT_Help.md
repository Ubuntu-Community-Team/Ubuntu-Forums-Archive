---
title: "Multiboot Vista SP1 x64 GPT Help"
date: 2017-02-13
forum: Windows
---

### Post by RocknRollTim on 2017-02-13
Hi all,


I have searching high and low on the Internet for a solution to fix *** STOP: 0x0000001E (0xFFFFFFFFC0000005,0xFFFFF80003ACC7,0x0000000000000000,0xFFFFFFFFFFFFFFFF) but can't find a way to make Vista SP1 x64 work alongside other Windows x64 OSs such as Windows 7 x64, Windows 8 x64, Windows 8.1 x64 and Windows 10 x64 using the controversial method i.e. using separate partitions. I was wondering whether Ubuntu can bypass this issue and if so how? I read up that one user on one forum stated that a third party software is required to get Vista to boot up alongside other Windows OSs. Your help would be much appreciated.


Kind regards,


RocknRollTim

---

### Post by howefield on 2017-02-13
Moved to the "*Windows*" forum.

---

### Post by yancek on 2017-02-13
Vista and newer versions of windows all use BCD as the bootloader.  Have you used bcdedit to create an entry for vista?  Which system has the primary bootloader?  You should be able to edit the boot files with bcdedit to add an entry for vista.   How many versions of windows do you have? You mention 5 in your post.  Do you actually have them all installed?  Are you using an MBR system to boot?

---

### Post by oldfred on 2017-02-14
Newer Windows versions typically are UEFI on gpt partitioned drives. But can be BIOS on MBR(msdos) partitioned drives.
But Windows only boots from gpt with UEFI.
And only fromMBR with BIOS.

And I thought Vista only booted in UEFI with the very last or perhaps it was an Enterprise version?
Windows 7 default install from DVD is BIOS/MBR only, but you can copy to flash drive and make it UEFI boot/install.

If BIOS best if all Windows installs are on primary partitions. But Windows only boots from one primary NTFS partition with the boot flag. Other installs can be on logical partitions but must boot thru the primary NTFS.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Why would anyone now want Vista?

---

### Post by RocknRollTim on 2017-02-14
Hi howefield,


Sorry for posting in the wrong forum and thank you for moving my thread into the correct forum.


Regards,


RocknRollTim

Hi yancek,


Thank you for getting back to me, I haven't used bcdedit to create an entry for Vista, don't even know how to use it as I haven't used it before, is it something you can direct with me or is it a question for someone on one of the Microsoft forums to help me with? Which version of bcdedit would you advise me to use? Vista or 10? With regards to the primary bootloader its the Vista one but Windows 10 is the default OS to boot to. I have 6 versions of Windows installed even though I said 5 in my initial post and were initially installed in the following order until I reinstalled Vista to try to resolve the BSOD, Windows Vista Ultimate SP1 x64 > Windows 7 Ultimate x64 > Windows 7 Professional SP1 x64 > Windows 8 Pro > Windows 8.1 Pro > Windows 10 Pro. I do currently have them all installed. I am using the GPT system to boot as I have a 4TB SHDD installed and want to make full use of the full capacity as well as the 128 partition capacity as MBR has limitations where drives above 2.2TB can't be fully utilised and only allow a maximum of 4 partitions to be created.


Kind regards,


RocknRollTim

Hi oldfred,


Thank you for getting back to me and for posting the information, I think I have got some clarification on what to do but would you advise me to try bcdedit first as suggested by yancek? I am using the GPT partition system as previously explained to yancek, each OS is using a separate partition i.e. 120GB for each OS apart from Windows 10 which is using 1.5TB with keeping the not allocated space on standby in order to expand partitions in the future. All of this information is hosted on a basic disk. Vista SP1 x64 was the first build to allow booting to UEFI and not the original x64 build as well as XP x64, this applied to all original x64 editions of Vista. I only know this as I tested these with my PC using the current configuration. Reason why users use Vista is down to personal preference.


Kind regards,


RocknRollTim

---

### Post by oldfred on 2017-02-14
You only normally have one ESP - efi system partition and Windows has its boot file bootmfgw.efi and BCD in the /EFI/Microsoft folder. And then BCD has other Windows installs.
Grub will only see the one install and offer to boot it, but then BCD will show other Windows installs.
You do nave to make sure newer Windows fast start up or hibernation is off, even if just multiple booting Windows.


But I have seem some play with multiple ESP, but only keep one active at a time. Not exactly sure how that works.

---

### Post by RocknRollTim on 2017-02-15
Hi oldfred,

When I initially installed Windows Vista SP1 x64, a System Reserved partition (Partition 1) as well as an ESP partition (Partition 2) was created when creating a partition for Vista (Partition 3) and created the other partitions afterwards using the same wizard i.e. Partition 4 for Windows 7 Ultimate x64, Partition 5 for Windows 7 Professional SP1 x64, Partition 6 for Windows 8 Pro x64, Partition 7 for Windows 8.1 Pro x64 and Partition 8 for Windows 10 Pro x64. However when I came to install Windows 7 Ultimate x64 on Partition 4, the System Reserved partition as well as the ESP partition were not visible, the same happened installing the rest of the Windows OSs as well as reinstalling Windows Vista Ultimate SP1 x64 on Partition 3 which changed the bootloader as well as adding another boot entry for Vista in the bootloader which I got rid of using msconfig in one of the Windows OSs, presume this is normal behavior? Need to look into these options a bit more before attempting further.

Kind regards,

RocknRollTim

---

### Post by oldfred on 2017-02-15
Never installed multiple Windows.

But I thought it best to always install from oldest to newest as older install will not know about newer versions and may not find them.
And always back up ESP if UEFI or system boot partition if BIOS before each additional install.

I also thought after install Windows does not mount ESP.

---

### Post by RocknRollTim on 2017-02-15
Hi oldfred,

I installed the Windows OSs in order from oldest to newest but Vista still displays when BSOD when booting up.

By the way how do you back up the ESP? Sorry to ask 21 questions.

I am only aware that the ESP partition is created after the first primary partition is created but will continue to look into both methods.

Regards,

RocknRollTim

---

### Post by oldfred on 2017-02-15
With BIOS you always had to install boot loader to MBR, and that was so tiny other places on hard drive had more boot data.

With UEFI, most of boot data is in ESP.
And you can just backup & restore ESP to have fully bootable configuration.
UEFI is supposed to auto find the .efi boot files in the folders in the ESP. But many only find the Windows entry.
And UEFI stores boot entries in NVRAM, so if you remove a drive & restore it, you often have to update NVRAM.
And UEFI uses gpt's GUID to find ESP, so if reformatted, you have to update NVRAM.

You can reinstall grub to update Linux boot entries.
Or use efibootmgr, best to see if duplicated entries or other issues. Some early UEFI crashed if NVRAM over 50% full, and system was totally bricked. They originally blamed Linux, but issue occurred with Windows and additional UEFI entries, so turned out to be vendor's implementation of UEFI.

From Ubuntu this shows UEFI boot entries. No idea how to do from Windows.
sudo efibootmgr -v
man efibootmgr

---

### Post by RocknRollTim on 2017-02-16
Hi oldfred,

Sorry for the delay in getting back to you and thank you for your response, will also look into these options before attempting. 

Regards,

RocknRollTim

---

### Post by yancek on 2017-02-16
The link below has an explanation on using bcdedit to add entries.  It starts out discussing installing Ubuntu dual-boot and adding an entry for it after using dd to get the IPL so you can skip all that.  Similar process used to add a windows entry.  My notes on adding windows 7 to windows 10 boot menu below:

Opened Disk Management in windows 10 to get windows 7 drive letter which was E.  You would need to do this to determine which partition windows 10 sees vista on.  Used the command below to create an entry for it which also set it as default or first option:

bcdboot E:\windows  (If your vista does not show as drive E, you need to replace E with whatever it is)

Then used the following command to add it to the end of the menu, using the UUID for it which 
showed in the bcdedit menu:

bcdedit /displayorder {ID} /addlast (Insert the actual UUID to the left where you see {ID}

Good luck.

---

### Post by RocknRollTim on 2017-02-16
Hi yancek,

Will definitely try the instructions in your last post, thank you for getting back to me again.

Regards,

RocknRollTim

Hi yancek,

I am reporting back to let you know that the last load of commands in your post did not resolve the boot issue with Vista.

Regards,

RocknRollTim

---

### Post by yancek on 2017-02-17
I just noticed that I referred to a link in an earlier post and forgot to post the link so here it is.  You need to scroll down a bit to get to the bcdedit commands.

[https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

I don't actually use windows and only went through this process one time so my notes are a little cryptic.  I think you may need to use the "bcdedit set" command explained at the link above.  Also, I did this on an MBR machine and don't have any idea if this will work with vista on EFI.  Good luck.

What happened when you ran the bcdboot command?  My recollection of when I did it is it output something like boot files created.

---

### Post by RocknRollTim on 2017-02-18
Hi yancek,

Thank you for getting back to me, will follow the link in your last post and to let you know how I get on. When I ran the commands in your previous post, the following outputs were displayed after each command was initiated.

C:\Windows\system32>bcdboot D:\windows
Boot files successfully created.

C:\Windows\system32>wmic csproduct get uuid
UUID
4C4C4544-0044-5610-8054-C3C04F44354A

C:\Windows\system32>bcdedit /displayorder {4C4C4544-0044-5610-8054-C3C04F44354A} /addlast
The operation completed successfully.

D is where Vista files are located. Used following link [https://www.nextofwindows.com/the-best-way-to-uniquely-identify-a-windows-machine](https://www.nextofwindows.com/the-best-way-to-uniquely-identify-a-windows-machine) to obtain UUID. 

Regards,

RocknRollTim

_Update_

I am now attempting to reverse engineer the problem by reinstalling each OS one at a time in order of oldest to newest using separate partitions, I can remember Vista working up until the point when I put on Windows 7 in which it performed a Check Disk during install of Windows 7 and wasn't sure whether this amended the partition table. Will keep you posted.

---

### Post by oldfred on 2017-02-18
Be sure to backup ESP - efi system partition after each install.
And/or compare /Boot/BCD after each install.

---

### Post by yancek on 2017-02-18
When you ran the following command, did you see a new entry for vista when you run bcdedit?  Looking through my notes again, that's all I had to do to get the windows 7 entry which did boot.  vista with SP1 should work with EFI per the microsoft site.

> C:\Windows\system32>bcdboot D:\windows

---

### Post by RocknRollTim on 2017-02-18
Hi yancek,

With regards to running bcdedit as instructed previously, there was already a boot entry for Vista in which the entry wasn't duplicated and was reused. Unfortunately I cannot use the command you suggested in your last post at present as I am now in the process of a total reinstall. Will keep on testing and consider all that has been suggested so far.

Regards,

RocknRollTim

[FONT=arial][COLOR=#141414]_Update_
[/COLOR]
[COLOR=#141414]Discovered that Windows OSs beyond Windows 7 break the Vista boot, I'm now assuming its because of the latest boot loader, not unless I change the boot order using bcdedit but I'm not sure whether that would change the boot loader back to the classic boot loader though.[/COLOR][/FONT]

---

### Post by yancek on 2017-02-18
Windows systems beginning with vista all use bcd as the bootloader.  I'm sure there are minor changes from version to version but it is basically the same bootloader with the same boot files.  The difference with windows 8 and 10 is UEFI which is the default.   Although UEFI is not default with vista and 7, you should be able to use UEFI with both.  I don't use UEFI so I'm not familiar with the process or boot files.  I would suggest checking the support.microsoft site or a windows forum.

---

### Post by RocknRollTim on 2017-02-19
Hi yancek,

When I was referring to the boot loader in my last post I was meaning the classic and metro boot menu, I will consult the microsoft.support website or Windows forums as suggested. Thank you for your help and information.

Regards,

RocknRollTim

[COLOR=#000000][FONT=&amp]_Update_
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Even temporarily removing the boot entries for Windows 10, 8.1 and 8 using EasyBCD didn't work which I would have expected to work.

[/FONT][/COLOR][COLOR=#000000][FONT=&quot]P.S. I found this link [/FONT][/COLOR][https://neosmart.net/wiki/repair-dual-boot-configuration/#Repair_Windows_Vista_on_a_dual-boot_system](https://neosmart.net/wiki/repair-dual-boot-configuration/#Repair_Windows_Vista_on_a_dual-boot_system)[COLOR=#000000][FONT=&quot] whilst I was on the Internet which unfortunately is for MBR, however the other thing I have noticed when logging in to each Windows OS is that the drive letters in Windows Explorer change slightly each time, this should have nothing to do with it surely?  [/FONT][/COLOR]

---

### Post by oldfred on 2017-02-19
I believe which ever Windows you boot into will always be C:.

Generally EasyBCD is not necessary for UEFI boot. 
Some like it for BIOS boot, but if booting with Ubuntu if forces you to install grub in an unreliable way (to PBR) and uses the very old grub4dos to chainload to grub2.

---

### Post by RocknRollTim on 2017-02-19
Hi oldfred,

I can confirm that C is the default drive letter when I boot into Windows regardless of which version.

I feel I should give GRUB2 EFI a shot and see if it fixes the issue, I have got nothing to lose as everything I need is backed up anyway. 

Regards,

RocknRollTim

_Update_

Installed Ubuntu using some of the instructions from the following link [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352), used 32000MB for swap area and 120000MB for Ubuntu primary partition but according to the link I should have chosen logical for the Ubuntu primary partition but may have misinterpreted the instructions though. However the problem I have got now is that the PC boots to the GRUB2 menu instead of the Windows Boot Manager and have to go through the GRUB2 menu, not sure whether I selected the EFI version of GRUB2 though as I selected Ext4 journaling file system for the setup of the Ubuntu primary partition plus Vista still comes up with the same BSOD as before when using the Windows Boot Manager i.e. now the classic bootloader instead of the Metro bootloader.

---

### Post by oldfred on 2017-02-19
With UEFI, grub only boots the one Windows entry in the ESP.
Your other alternative is multiple ESP.

UEFI and install will only boot from one ESP or the FAT32 with boot flag.
But you can have multiple FAT32 partitions and with each or several installs move boot flag and set that as default boot.
You then may be able to have grub boot all of them.

 Dual boot two Windows UEFI from grub, two efi partitions.
[http://askubuntu.com/questions/653101/boot-repair-windows-not-listed](http://askubuntu.com/questions/653101/boot-repair-windows-not-listed)

---

### Post by RocknRollTim on 2017-02-19
Hi oldfred,

Will give the link a try from your last post but will rest and absorb this lot for tonight though.

Regards,

RocknRollTim

Hi oldfred,

So what you are suggesting in your last post is to start again? If so, I was thinking of taking the setup from several angles and are as follows, 1) Create partitions using Ubuntu partition wizard i.e. one primary swap area, one logical/primary partition using Ext4 journaling file system and six primary partitions using FAT32 in order to install Windows OSs or 2) Install Windows Vista, create partitions using Ubuntu partition wizard i.e. one primary swap area, one logical/primary partition using Ext4 journaling file system and five primary partitions using FAT32 in order to the remainder of Windows OSs or 3) Install Windows Vista, create partitions using FAT32 in Disk Management and install remainder of Windows OSs or 4) Follow steps from post 3 in link as previously supplied. If you advise to follow suggestion 4), do I have to repeat steps 2 to 6 in the link you previously provided using post 3 in order to install each remaining Windows OS? I have also been looking into a recovery tools package called EasyRE which apparently boot issues, not sure what your thoughts on this approach are. Lastly I was thinking of temporarily getting rid of Ubuntu so I can get rid of GRUB2 and for the Windows Boot Manager to appear again, what are your thoughts on this too?


Kind regards,


RocknRollTim

> **oldfred said:**
> Be sure to backup ESP - efi system partition after each install.
And/or compare /Boot/BCD after each install.

Hi oldfred,


Will consider your advice when reinstalling all the Windows OSs.


Regards,


RocknRollTim

---

### Post by oldfred on 2017-02-20
With gpt there are not primary, extended and logical partitions. They all are just one type or in effect primary.

If all but Vista work together you may only need two efi partitions.
But from UEFI only the one that has boot flag or is the boot,esp will be directly bootable. You can change which FAT32 is bootable, but would not be able to directly boot from UEFI all 4 installs.

Ubuntu is booting by finding files in the ESP/efi partition that you specify. I do not think it is at all checking that it is the official ESP, so should boot from any FAT32 that has the /EFI/Boot/bootmfgw.efi & BCD. Or from the fallback entry, /EFI/Boot/bootx64.efi.

---

### Post by RocknRollTim on 2017-02-20
Hi oldfred,

Thanks for getting back to me, I will test and to let you know how I get on.

Regards,

RocknRollTim

Hi oldfred,


I'm trying to carry out the third instruction, do you know how to use gdisk in order to change the code of the ESP?

Kind regards,

RocknRollTim


1. Install the first Windows normally.
2. Boot to a Linux emergency disk (the Ubuntu installer in "try before installing" mode should work fine).
3. Change the type code of the EFI System Partition (ESP) to something that Windows will ignore. gdisk is most flexible about this, since you can set the type code to anything you like, such as 8300 (the code used by Linux). You might optionally change the type code of the Windows partition, too, to keep it out of the second installation's boot loader. If you use gdisk, be sure to save your changes with w.
4. Install your second Windows. The installation should create a second ESP on the disk, and your computer should boot to this version of Windows. (If you did not hide the first Windows by changing its type code, it will probably show up as an option in the Windows boot loader.)
5. Boot the Ubuntu installer in "try before installing" mode again.
6. Change the type code on the first ESP back to the right thing (EF00 in gdisk). If you changed the type code of the first Windows partition, change it back (to 0700 in gdisk) at the same time.
7. Run the Ubuntu installer and install Ubuntu.

---

### Post by oldfred on 2017-02-20
The author is Rod Smith creator of gdisk.

GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by RocknRollTim on 2017-02-20
Hi oldfred,

I'm following the links you sent me but everytime I enter gdisk in Open Terminal it asks me for a device name, do you know I can find this?

Kind regards,

RocknRollTim

---

### Post by oldfred on 2017-02-20
More specific commands:
 Change type code  to 8300 with dual booting with Windows on gpt
[http://www.rodsbooks.com/linux-fs-code/index.html](http://www.rodsbooks.com/linux-fs-code/index.html)
sudo gdisk /dev/sdd
Command (? for help): t
Partition number (1-3): 2
Current type is 'Microsoft basic data'
Hex code or GUID (L to show codes, Enter = 8300): 8300
Changed type of partition to 'Linux filesystem'
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) 

Device name in Linux is usually /dev/sdX where X is drive sda, sdb, etc

All the commands are here or with ? when at Command:
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html) 

Other commands to know are v for verify, w for write/save, q for quit without save, p to print or show current partitions.
When you make a change use p to view, and either w if it looks correct or q to quit.

---

### Post by RocknRollTim on 2017-02-20
Hi oldfred,


Sorry to be a nuisance but after I enter sudo gdisk /dev/sdd, it says that there is only MBR present and when I enter p it only shows the flash drive where I'm booting Ubuntu from. I've tried entering sudo gdisk \\.\physicaldrive0 as instructed in the guides after coming out of gdisk completely but keeps coming up with an error 2. Your continual help would be much appreciated.


Kind regards,


RocknRollTim

---

### Post by oldfred on 2017-02-21
I used example with sdd.
What drive are you using sdd, or sda, sdb or sdc?

Post this:
sudo parted -l

If you want partitions list directly with gdisk you can also use this:
sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb
etc

---

### Post by RocknRollTim on 2017-02-21
Hi oldfred,

Thank you for getting back to me, will try your suggestions and to get back to you if I have anymore queries.

Regards,

RocknRollTim

---

### Post by oldfred on 2017-02-21
If you have multiple disks, would it not be easier to install Windows on different drives?

But installing Ubuntu in UEFI mode on second drive is not the easiest, do not know about Windows.

---

### Post by RocknRollTim on 2017-02-21
Hi oldfred,

I could do but want to see how I get on with the one drive first before installing another.

Regards,

RocknRollTim

---

### Post by LostFarmer on 2017-02-21
To add some info.  I have a multiboot with Win8.1, Win10-Home and Win10-Pro, each has its own boot folder in the ESP/EFI/ folder with names as win8.1 , win10-home and win10-pro.  Boot is controlled by 3 different menu entries in grub.cfg (manually edited). 

Each /EFI/win*/Boot/bcd file [I]I edited to remove all other boot entries.  One downside is the correct bcd store is not placed in the registry , so far no real problem.  The only bcd store used by a booted Windows is ESP/Microsost/Boot/bcd, so the registry  nor bcdedit will  see the bcd store in the 3 /win*/boot/bcd that I use (with correct commands the correct bcd can be editd).  When WIndows is updated it may create EFI/Microsoft/Boot/bcd and it will be the one seen by running bcdedit or looking in the registry, but no problem, as long as one remembers.

I have no knowledge with Vista, win7 or mult-hdds.
[/I]

---

### Post by RocknRollTim on 2017-02-21
Hi LostFarmer,

Thank you for sharing that with us, hopefully one day I will have a multiboot that will work including Vista, determined to get it working.

Regards,

RocknRollTim

Hi oldfred,

Just to let you know I performed the steps below to try to rectify the BSOD when booting into Vista and resulted in the same BSOD, does this mean I'll have to install another drive just to run Vista?

1. Installed Vista which created the ESP partition for UEFI.
2. Hid the Vista OS partition using parted and gdisk.
3. Installed Windows 8 which updated the ESP partition for UEFI.
4. Unhid Vista OS partition using parted and gdisk.
5. ESP revealed entries for all systems.

Regards,

RocknRollTim

---

### Post by oldfred on 2017-02-23
When you say you hid, did you change the ESP from the original one to a new one?
By removing boot,esp from ESP FAT32 partition?

If so then I do not know how Windows found the first ESP?

---

### Post by RocknRollTim on 2017-02-24
Hi oldfred,

There were 3 partitions for Windows Vista, one for System, one for MSR and another for Primary, each of these were created using the default Windows file system NTFS before temporarily changing the Hex code or GUID for the Primary partition and installing Windows 8 afterwards, are you saying I should have formatted the partitions as FAT32 first before temporarily changing the Hex code or GUID for the Primary partition and installing Windows 8 afterwards?

Kind regards,

RocknRollTim

---

### Post by oldfred on 2017-02-24
These should be the standard partitions. I think the recovery partition is something new with Windows 10 and is just after the main install or "Windows" partition.

[https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

The Windows system partition (which to me is an incorrect term, as system should be main install) should be the ESP - efi system partition FAT32 formatted. With parted or gparted it have boot flag and shows esp,boot. With gdisk it has code ef00. Not sure how Windows shows it.
And that is the partition that you must change to a standard data partition, so Windows creates a new FAT32 ESP. It should not install boot loaders into a standard data partition even if FAT32.

---

### Post by RocknRollTim on 2017-02-24
Hi oldfred,


Thank you for posting the link regarding recommended partition configurations for Windows 10, I can confirm these configurations were used for Windows 10 on my PC.


I'll have another look at the partition configurations for Windows Vista but don't recall seeing the ESP partition though, maybe because I didn't format the newly created partition for Vista as FAT32, will try this when I get back and report back as soon as I have tested.


Regards,


RocknRollTim

---

### Post by oldfred on 2017-02-24
If you do not have an ESP - efi system partition then it would be a standard BIOS/MBR install.

---

### Post by RocknRollTim on 2017-03-05
Hi oldfred,

Sorry for the delay in getting back to you, you are right with what you are saying, you cannot format a GPT volume as FAT32, would this still be the case if I was to format the volume as FAT32 using Ubuntu?

Kind regards,

RocknRollTim

P.S. Apologies for the duplicate posts last weekend, there was a problem with the connection I was using at that time as I wasn't at home when responding to your posts i.e. wouldn't appear under the thread even when refreshing the page and kept saying the Ubuntu forums were down when in fact they weren't, this was probably due to the fact the connection was slow.

---

### Post by oldfred on 2017-03-05
I do not know Vista, but my old XP was NTFS. Only early copies of XP would work on a FAT32 formatted partition.

Only some versions of Vista would work on gpt partitioning. You have to install in UEFI boot mode and at least a 64 bit version.
Windows 7 DVD was BIOS only, and had to be copied to a flash drive and files moved around to create a UEFI bootable version. How you boot installer is then how it installs.

---

### Post by RocknRollTim on 2017-03-05
Hi oldfred,

FAT32 is a file system that can be used with a lot of versions of Windows (Windows 95 and onwards) except you can't use it on a disk that uses GPT, I have so far found that versions of Vista which don't support GPT are the original and SP2. I am now in the process of trying exFAT as this is the only file system I haven't tried unlike NTFS and FAT32 which I have.

Regards,

RocknRollTim

---

### Post by oldfred on 2017-03-05
[https://en.wikipedia.org/wiki/ExFAT](https://en.wikipedia.org/wiki/ExFAT)

Exfat is primarily for flash drives. And flash drive devices are not Windows bootable.
Also ExFAT is Microsoft proprietary.

---

### Post by RocknRollTim on 2017-03-05
Hi oldfred,

Thanks for sharing the info on exFAT, I created a partition using diskpart and formatted it as exFAT but after I installed Vista on that partition it converted it back to NTFS? I really thought this would work due to being Microsoft proprietary and supports up to 128 Pebibytes or 512 Tebibytes? I guess it looks like NTFS is always going to be the default file system regardless of choosing another file system beforehand in order to install Windows.

Regards,

RocknRollTim

P.S. I created the partition in the partition screen and formatted the partition as FAT32 using diskpart, however I forgot to close diskpart and to refresh the partition screen before installing Windows hence why Windows Vista installed as NTFS.

_Update_

I have concluded that this experiment is currently not possible on a GPT volume with Windows Vista and can only be either achieved using one or more MBR/GPT volumes or by using virtual emulators. If anyone can find a way round this problem please feel free to post your resolutions in this thread.

---

### Post by RocknRollTim on 2017-06-21
_Update_
 
I went down the path of EasyBCD for a few months and wasn't able to rectify my issue, I figure its because my PC drivers aren't officially supported by Windows Vista hence why I was experiencing unpredictable behaviour with Windows Vista alongside Windows 8 and above plus not to mention why I wasn't able to get any drivers to work with Windows Vista when operating independently without any incompatible OSs alongside such as Windows 8 and above. I therefore conclude that my experiment I was wanting to achieve cannot be carried out successfully without getting a PC that supports EFI or UEFI from the years 2005 or 2006, that's if I can find one of course, if not, looks like I will have to result to a hypervisor to run the OSs I want to experiment with but saying that this method doesn't give a sense of realism when it comes to testing incompatibility of drivers. The PC I was testing with was a Dell Vostro 470.

---

