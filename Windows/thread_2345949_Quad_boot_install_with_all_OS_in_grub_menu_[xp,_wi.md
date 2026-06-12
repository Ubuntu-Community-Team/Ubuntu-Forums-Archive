---
title: "Quad boot install with all OS in grub menu [xp, win7,win10, ubuntu]"
date: 2016-12-09
forum: Windows
---

### Post by jarrod4 on 2016-12-09
I have a test machine that I would like to run 4 OS images in (yes I know how to build and run VM's). I rebuilt the machine this morning by installing XP, then win7, then win 10, then ubuntu. When I boot I can either boot into ubuntu, or I can select the win10 bootloader from grub.  From inside the win10 bootloader I can then select the windows OS I want to run. 

I know meierfra had written up some good instruction in the following thread

[https://ubuntuforums.org/showthread.php?t=1362297](https://ubuntuforums.org/showthread.php?t=1362297)

I had followed them yesterday with my test machine and at the end I screwed something up in step 4.  The OSes (XP, win7, win8, ubuntu) would show up in grub, but when I went into my windows 8 it would no longer boot.  So, i nuked win7, win8, and ubuntu and reinstalled this morning. Just wanted to see if I have any sugestions on wha tI need ot dd to get it working.  

Thank you.

---

### Post by oldfred on 2016-12-09
Are all Windows in primary NTFS partitions?
XP uses boot.ini, but all the newer versions use BCD.
And PBR or partition boot sector must refer to ntldr for XP and bootmgr for later versions.
I have run Windows 7 chkdsk on my XP install and it converted PBR to bootmgr version. I then had to run chkdsk from XP or use testdisk to restore backup PBR to boot my XP.

Are you moving boot flag before installing second version of Windows?

---

### Post by jarrod4 on 2016-12-29
Sorry, just getting back to this:

Are all Windows in primary NTFS partitions? - Yes

XP uses boot.ini, but all the newer versions use BCD.
And PBR or partition boot sector must refer to ntldr for XP and bootmgr for later versions.
I have run Windows 7 chkdsk on my XP install and it converted PBR to  bootmgr version. I then had to run chkdsk from XP or use testdisk to  restore backup PBR to boot my XP.

Are you moving boot flag before installing second version of Windows? - No

Each windows install was in a 20G primary partition with the oldest version of windows (XP)  installed first.  Subsequent versions were simply installed from the actual install disc media to the appropriate partition.  The last software installed was Linux in an extended partition.

---

### Post by oldfred on 2016-12-29
Then each newer install of Windows saw boot flag on XP partition and installed its boot files and converted PBR to its type(bootmgr).

You may be able to move boot flag, and run full set of Windows repairs starting with newest first. With newest last installed one, you may be able to just copy bootmgr & /boot/BCD to its partition. Grub will find it. But that copy of BCD will still refer to all copies of Windows.

Grub2's os-prober looks for boot files, not boot flag. Windows boot loader only looks for boot flag and expects to find more boot code in PBR - partition boot sector.
But you have to make sure Windows 10's fast start up or always on hibernation is off.
        Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
If repairs work, then reinstall should not be required.
       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by jarrod4 on 2016-12-29
[INDENT] 					Thank you again for the info.  I had it working with XP, win7, win 8 preview, and ubuntu 12. I nuked about half the box and wiped win7 for a re-install, removed win8 and installed win 10, and re-installed unbuntu from scratch.

I had found an old thread with you and [**[COLOR=#000000]meierfra.[/COLOR]**]("https://ubuntuforums.org/member.php?u=552151") which seemed to get me most of the way there the first time.  The issue I have right now is that when I select windows 10 from Grub it just comes right back to the grub menu.  I've got to sort out what is wrong there first.  After that I think its may be a matter of modifying the directions I coped below from [**[COLOR=#000000]meierfra.[/COLOR]**]("https://ubuntuforums.org/member.php?u=552151") The only issue is that the instructions only cover 

Edit:  The same instruction work for Windows 7. Just replace Vista by "Window7" everywhere.

Try this
[SIZE=3][COLOR=blue] Boot into Vista.[/COLOR][/SIZE]

[B]Step 1 Edit the Vista boot loader
[/B]
Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open a Vista commandline as an administrator. Type

 	Code:
 	  
bcdedit /set {bootmgr} device boot
bcdedit /set {bootmgr} timeout 0
bcdedit /delete {ntldr} /f 
(don't close the command line)

**Step 2 Fix the XP bootsector.**

Insert your Vista DVD in the DVD drive and wait for a few second. (If  you don't have a Vista DVD/CD let me know and I can show you different  ways to accomplish this step)
At the command line: 
 	Code:
 	E:\boot\bootsect  /nt52 D: /force 
Here "E" needs to be replaced by the drive letter of your DVD  drive and "D" by the drive letter of your XP partition. (Just look in  "My Computer" to determine the drive letters. Even if you know the drive  letters, I suggest to double check. Vista and XP probably use different  drive letters. You need to use the drive letters used by Vista)


[SIZE=3][COLOR=blue] Boot into Ubuntu.[/COLOR][/SIZE] 
and open a terminal (Applications->Accessories->Terminal) 


** Step 3 Add Vista to "menu.lst" **

Open menu.lst via


 	Code:
 	gksudo gedit /boot/grub/menu.lst 
Your current entry for Vista will later actually boot XP. So you  might want to edit the title. Also you should create a similar entry for  Vista. (if you need help with that post the output of "sudo fdisk -lu")



** Step 4  Move the boot files from XP to Vista **

Type 

 	Code:
 	 sudo fdisk -lu 
and determine the device name of the XP partition and the device name of the Vista parition.
In the following I assume that  XP is on /dev/sda1 and Vista is on /dev/sda2. 

 	Code:
 	 sudo mkdir /mnt/{XP,Vista}
sudo mount /dev/sda1 /mnt/XP
sudo mount /dev/sda2 /mnt/Win
sudo mv /mnt/XP/{Boot,bootmgr} /mnt/Vista 
Of course you need to  replace  /dev/sda1 by the device name of  the XP partition and /dev/sda2 by the device name of the Vista  partition. 
Sometimes the directory  Boot  is called BOOT instead. Use  "ls -l /mnt/XP" to determine the correct spelling. 


Reboot and hopefully you will be able to boot into all your OSs from the Grub menu. 				
[/INDENT] 			
  			   		
 			 			 			[INDENT] 				 					Last edited by meierfra.; December 23rd, 2009 at 03:04 PM. 				 				 			
[/INDENT]

---

### Post by oldfred on 2016-12-29
Moving to Windows sub-forum since mostly Windows issues.

Back when meierfra posted those Windows fixes, Windows 8 or 10 was not yet out.
Since Windows 8, Microsoft implemented "fixes" to get Windows to boot faster. Windows does not really boot any faster, but they made vendors add SSD, UEFI fast boot which skips all the checks for hardware changes, and added fast start up which really is just hibernation. All those changes sped up boot process but had nothing to do with actual time Windows takes to boot.

The fast start or hibernation (whether UEFI or BIOS) interferes with being able to read NTFS partitions from another system, even other Windows. It leaves all mounted (all) NTFS partitions in the hibernated state. The Linux NTFS driver will not then mount nor then can grub find boot files in Windows to enable booting. That is to prevent damage as writing into a hibernated file system may corrupt it. 

Not sure then how your Windows 7 will work if hibernated by Windows 10? Best to make sure you have fast start up & hibernation turned off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by jarrod4 on 2016-12-29
understand the issues with hibernation, and I will fix them as soon as I get the system booted. 

The key issue I am trying to resolve right now is getting grub to show a selection for each of the operating systems, and for them to be able to boot from the grub menu.  Right now it will only show the boot loader 

sudo os-prober
/dev/sda1:Windows 10 (loader):Windows:chain

/devsdaa1 - XP
/dev/sda2 - win7
/dev/sda3 - win10
/dev./sad4 - Linux

---

### Post by oldfred on 2016-12-29
That is because Windows only has boot files in sda1. And that should be your Windows 10 if last installed. And then from Windows 10's BCD you have the choice to boot each copy of Windows.

Until you get boot files bootmgr & BCD in each of the newer Windows grub will not boot them directly.

---

### Post by jarrod4 on 2017-02-09
Just wanted to give an update on this. I had made the mistake of copying the boot files to drive C: (win XP) and setting the boot flag for that drive.  The system would not boot in that configuration no matter what I tried.  I moved the flag back to drive e: (win 10), and copied the boot directory back and the system would then boot, and in the boot menu show the three version of windows (XP, 7, and 10), and it will boot into each of them from the menu.

When I was playing with bcdedit I had ended up writing over GRUB which I had to fix to get Ubuntu working. Before doing so I copied the boot directory into each installation.  When I installed GRUB, it picked up on the OS installs and created a menu entry for each of them.  However, when you select them from Grub, they will not start.  If you boot to win 10 from Grub, you can select the OS from the win 10 menu and boot into it. So, I still have that to sort out getting the direct entry from GRUB working.

---

### Post by yancek on 2017-02-09
windows needs boot files on a primary partition.  If you had xp on sda1 and wanted to then install windows 7 on sda2, before beginning the install, mark sda2 as the active partition and use the manual install method, referred to as 'custom' install I believe.  Repeat the process for windows 10, mark sda3 as active and use the custom install option to install windows 10 to sda3.  Using this method, the separate boot files for xp, win7 and win 10 are on their respective partitions and you should be able to run update-grub and get separate menuentries for each system.  Since you are using an MBR partition, you have only 4 primary partitions available and if you have an Extended partition, that will be one of the primary.  If the installation of either win 7 or win 10 was to a logical partition, it will install it's boot files to the active primary which would be xp.

If you still want help with this, it might be useful to post more details such as what you get when running boot repair downloaded from the link below.  Don't do any repairs, just select the option to Create bootInfo summary and post a link to the output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2017-02-09
You may have to move boot flag to each install, and then using that version's repair/install repair console to run a full set of updates. 
Then that versions should directly boot. 

After all versions of Windows are fixed, then restore grub as default boot.

Grub only boots working Windows, although a few have said pressing Windows entry & f8 at almost same time did get them into the repair console, but they had to try many times as too little time normally. Better to have repair disk or installer with its repair console.

---

