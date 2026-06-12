---
title: "Can't Boot Windows after dual-boot installation with Lubuntu"
date: 2023-04-16
forum: Windows
---

### Post by arius88 on 2023-04-16
A bandmate recently gave me a computer with Windows 7 Professional (BIOS) on it. I need to keep Windows because a) my bandmate may want the machine back some day, and b) it contains the professional version of a recording program that he uses to record and mix our songs.  

However, I prefer Linux, so I decided to turn the computer into a dual-boot machine. I was able to partition the drives and install Lubuntu. Lubuntu works great. However, now I can't boot into Windows. If I press F12 on startup, a menu comes up with an option to boot Windows 7. I click on it, and I get an error. "Windows failed to start. A recent hardware or software change might be the cause." It then prompts me to install a Windows installation disk, which I don't have. It gives me two other potentially useful pieces of information:

Status: 0xc0000225

Info: The boot selection failed because a required device is inaccessible.

Obviously the Lubuntu install changed something that is causing Windows not to boot. But I have no idea what. 


Q1: Any idea what's going on or how to fix it? Is there a way to undo this and get Windows back?
Q2: Can I acquire any old copy of a Windows 7 installation disk and use that to try to fix the issue, or does it have to be the exact system disk from the original install (which I am confident I will never be able to track down)? 

Thank you for reading and any advice or ideas.

P.S. Edited to add that I googled the status error code thingy "0xc0000225" and this link came up: [https://learn.microsoft.com/en-us/troubleshoot/azure/virtual-machines/boot-error-status-not-found#add-the-osdevice-variable](https://learn.microsoft.com/en-us/troubleshoot/azure/virtual-machines/boot-error-status-not-found#add-the-osdevice-variable). Looks useful but unfortunately I have no idea how to do any of it. It seems to assume I can load DOS or something and tells me to enter a bunch of commands... but how can i do that if i can't get Windows to load?

---

### Post by oldfred on 2023-04-16
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

BIOS installs on one drive, only have one MBR for boot loader. So you now have grub as your boot loader.
If Windows is working, you should be able to boot Windows from grub, if both systems are installed in BIOS mode.
If Windows needs repairs, you need your Windows repair/recovery flash drive.
You may be able to temporarily install a Windows boot loader to MBR, fix Windows, then restore grub to MBR.

With dual boot systems, you need both a Windows repair flash drive and Ubuntu live installer for current versions of installed systems to make repairs.

---

### Post by yancek on 2023-04-17
The link below gives several options which you should be able to use to download and use a windows 7 recovery disk.

[https://answers.microsoft.com/en-us/windows/forum/all/download-windows-7-64-bit-system-repair-disk/69ee4694-2a2c-4d6d-b92f-32a0ff98d25d](https://answers.microsoft.com/en-us/windows/forum/all/download-windows-7-64-bit-system-repair-disk/69ee4694-2a2c-4d6d-b92f-32a0ff98d25d)

The best way to get help is to use the boot repair tool suggested above, use the 2nd option explained on that page using the ppa and when you run boot repair, make certain to select the Create BootInfo Summary option and do not try any repairs.  I'm guessing you installed Lubuntu UEFI in which case it will not boot a Legacy install of windows 7 (the default).  If that is the case, you would need to reinstall Lubuntu in Legacy mode.  The boot repair output will give this information.

---

### Post by arius88 on 2023-04-19
Thanks for the responses. Ran the boot-repair thing Fred suggested! 
Pastebin is here: [https://paste.ubuntu.com/p/63yHTTwF58/](https://paste.ubuntu.com/p/63yHTTwF58/)

Did the suggested repair but upon reboot, the same error occurred. ("Windows failed to start. A recent hardware or software change might be the cause.")

Any thoughts on what I should do next?

---

### Post by oldfred on 2023-04-19
Grub only boots working Windows.
Windows in BIOS mode only boots from partition with boot files and boot flag, your sda1. But you have boot flag on sda4, so Windows fixes will not work. Move boot flag back to sda1, and then your Windows repairs may work.
Boot-Repair copied boot files to sda2, just as backup. Many users do not know Windows in BIOS mode has boot partition with boot files & delete it. Then very difficult to repair.

Boot-Repair used to have syslinux boot loader as option. That is a Windows type boot loader that uses boot flag & will boot Windows.
If in advanced mode you select the Windows install, and sda, it may offer to install syslinux boot loader. It only installs the part in MBR, not full syslinux configuration files. Boot flag still must be on sda1 first.
If Windows boots or needs repairs with F key, then reinstall grub with Boot-Repair's advanced mode, selecting Ubuntu and sda.

If Windows does not boot, then you have to use your Windows repair/recovery flash drive.

---

### Post by arius88 on 2023-04-21
Thanks for your help, Fred. I have a lot of questions, mostly about your second paragraph. But it seems the first order of business is to move the boot flag from sda4 back to sda1. I found some instructions here: [https://linuxconfig.org/how-to-set-or-change-boot-partition-flag-on-linux](https://linuxconfig.org/how-to-set-or-change-boot-partition-flag-on-linux). Will try that and report back.

---

### Post by arius88 on 2023-04-21
Actually, before I start messing around with fdisk, l could use a bit of guidance. Mostly just want to confirm my action plan:

1. Move boot flag from sda4 to sda1 using fdisk
2. Reboot and see if that worked, or nah? I'm wondering if just moving the boot flag will fix everything, but I'm concerned that if it didn't work, then I won't be able to boot back into Lubuntu to do any further Boot Repairing. Should I move the boot flag and then run Boot-Repair before rebooting?
3. Use Boot-Repair in Advanced Mode to... a) select Windows install + sda(1, or 2?) b) er... after that, you lost me. Do I want to install syslinux boot loader? Is it a problem about the lack of full syslinux configuration files or whatever you said there? I apologize, but I really don't know what most of this means.
4. If windows boots or needs repairs with F key... not sure what this means. I also have no idea how to reinstall a gub, but am assuming Boot-Repair has an option for that.... but again, Ubuntu and sda what? I have four partitions: sda1, sda2, sda3, and sda4. The first one (sda1) is for windows system stuff (100MB); sda2 (265.5GB) is for windows storage; sda3 (512MB) is for Lubuntu system stuff; and sda4 (199.7GB) is for Lubuntu storage.

To be clear, I did not delete my Windows boot partition (sda1).

Thank you. Just want to make sure I don't mess up my system any further by doing the wrong stuff.

---

### Post by oldfred on 2023-04-21
Moving boot flag does not change grub. Grub does not use boot flag.
Windows & some older boot loaders like syslinux (generic MBR) use boot flag.

With MBR, only the code in the MBR controls booting. Or you can either have grub in MBR or Windows in MBR. Windows will not boot Linux, so you normally want grub in MBR as it can boot Windows, but only boots working Windows.
With newer UEFI, you can always boot either system from UEFI boot menu, but with BIOS, it only jumps to MBR and code in MBR then starts boot process.
The syslinux boot loader is a full boot loader, and uses boot flag. But you do only need the tiny part of syslinux that is in MBR, so system jumps to the partition with boot flag to find more boot code. So syslinux in MBR will boot Windows. If using syslinux with Linux install, you would need the rest of the configuration files. 

Because you only have one MBR, you have to sometimes install Windows (or syslinux) boot loader to MBR to boot Windows & make repairs or turn off fast startup. Fast start up is a Windows default setting (since it is slooow). Windows will even turn it back on, with some updates. But fast start up sets hibernation flag & then the Linux NTFS driver will not use the partition to prevent damage to the NTFS partition. And then grub will not boot Windows and you have to put in the Windows type boot loader, fix Windows & restore grub.

Boot-Repair can restore grub. Its default fix is either update grub (menu) or reinstall grub. But you can use its advanced mode, choose an operating system and choose a drive to have it install a boot loader to MBR.
If Boot-Repair does not see the Windows install, then you have to use your Windows repair/recovery flash drive to repair Windows and/or install Windows boot loader.

I find it easier to move boot flag with gparted, but you can use any of many Linux tools or Windows to move boot flag. Some will remove boot flag when you add one to another partition. But I have seen some systems with two boot flags, so not all tools will remove the incorrect boot flag.

Boot-Repair Advanced mode screens
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by arius88 on 2023-04-21
Thanks for explaining all that, Fred. 

I am going to move that boot flag and then try using Boot-Repair in advanced mode. 

Two quick questions before I do that: 

1. What drive do I want to install the bootloader to MBR on - sda1? 
2. Is that safe, or is there a risk of nuking whatever Windows 7 bootloader was on there before I did all this dual boot stuff in the process?

Update: I figured out how to turn on the sda1 boot flag in KDE partition manager, but now I have a 3rd question...

3. Is it a problem if there are 2 boot flags enabled? ie Should I turn off the boot flag on sda4, or can I leave that on and just turn on the one for sda1? (It's currently greyed out in KDE partition manager, so I'm not even sure if I actually CAN turn the boot flag off on sda4.)

---

### Post by oldfred on 2023-04-21
Only one boot flag per drive, otherwise mass confusion.

You always install grub (or Windows) boot loader to a drive like sda, never to a partition like sda1.
If you install grub to a NTFS partition you break Windows as it has essential boot info in the partition boot sector.

I thought these commands only allowed one boot flag. 
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
sudo parted /dev/sda set 2 boot on

I used to use gparted, but I thought KDE was similar. But cannot easily  see settings for flags in my copy.

---

### Post by arius88 on 2023-04-22
Fred, I really can't tell you how much I appreciate all your assistance here. I'd be lost without you.

I tried entering the first of the commands you suggested:
sudo sfdisk -A2 /dev/sda

and got the following back

sfdisk: invalid option -- `2'

---

### Post by oldfred on 2023-04-22
Sorry this is just an example of the command. You have to replace sda with your drive and 2 with your partition. Probably should have posted this for sdXY. Added space, see below.
sudo sfdisk -A Y /dev/sdX
sudo sfdisk -A 1 /dev/sda

Your Windows boot partition is sda1.
But Boot-Repair copied essential boot files to sda2.
Windows does allow BIOS installs to not have boot partition and have only the one partition, so boot flag can work on either sda1 or should work on sda2. 
looks like space between N & partition number is required
[https://man7.org/linux/man-pages/man8/sfdisk.8.html](https://man7.org/linux/man-pages/man8/sfdisk.8.html)
man sfdisk

---

### Post by arius88 on 2023-04-22
Okay. So I tried

sudo sfdisk -A 1 /dev/sda

and got

"sfdisk: cannot open 1: no such file or directory"

After reading up on sfdisk a bit, I tried running 

sudo sfdisk -V sda

just to check on the partitions
and again it said "sfdisk: cannot open sda: no such file or directory"

Not sure if this is a syntax issue, or if I'm in the wrong directory (if i am, i have no idea what the right directory is or how to get to it), or whether there's something else going on. 

sfdisk -l clearly lists all four sda partitions, so obviously it can find the device when it wants to.

sda1
sda2
sda3
sda4

What am I doing wrong?

---

### Post by oldfred on 2023-04-22
You have to use full device. Almost all Linux commands are /dev/sda not just sda
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo sfdisk -V /dev/sda [/COLOR]
[COLOR=#000000]**/dev/sda:**[/COLOR][COLOR=#000000] [/COLOR]
No errors detected. 
Header version: 1.0 
Using 10 out of 128 partitions. 
A total of 601090579 free sectors is available in 6 segments (the largest is 286.6 GiB).
[/FONT]
```

I rarely use sfdisk. If using command line I use gdisk as I only use gpt partitions.
But normally use gparted as I have gui.

---

### Post by arius88 on 2023-04-22
Ah. Got the -V thing to work! No errors detected, so that's good. 

But why did "sudo sfdisk -A 1 /dev/sda" yield "no such file or directory"?

---

### Post by oldfred on 2023-04-23
I always install gparted, so have not used the command, but had it in my files.
I suggest gparted as I know it works.

You can use gparted on umounted partitions. But with old MBR, all logical partitions inside the extended partition are seen as mounted  if any partition is mounted. So normal suggest is to use live installer. Ubuntu has gparted. Or you can download a gparted live ISO.
I have two drives so install gparted to use on other drive. And with gpt I can add or modify any unmounted partition just not the mounted ones.

---

### Post by arius88 on 2023-04-23
Made a GParted live CD, running it now. 
Was quickly and easily able to change the boot flag to sda1 by right clicking on the partition and selecting "Manage Flags" and checking the Boot option. Awesome.

HOWEVER

As soon as GParted loaded the GUI or whatever with my partitions displayed, I noticed a warning label on sda1. (The other partitions seem to be fine.) Clicking on it yields the following information:

! Warning:

Unable to detect file system! Possible reasons are: 
-The file system is damaged
- The file system is unknown to GParted
-There is no file system available (unformatted)
-The device entry /dev/sda1 is missing

1. Should I be concerned about this, or is it just because it's a Windows partition?
2. What's my next move?

Edited to add: I found this article. Looks useful, but I'm a bit scared to try it. [https://www.diskpart.com/articles/gparted-fix-mbr-7201.html](https://www.diskpart.com/articles/gparted-fix-mbr-7201.html). It's advising me to use something called "testdisk." What do you think?

---

### Post by oldfred on 2023-04-23
Testdisk is good for recovering missing partitions. Or perhaps recovery of backup PBR - partition boot sector.

You have sda1, but it does not seem to see it as NTFS.
First you should try chkdsk from a Windows repair disk. If it also gives errors, it may be issue with PBR.
Partition table says NTFS. But Windows NTFS & FAT32 have essential info in the PBR partition boot sector (record). NTFS does have a backup PBR that can be recovered with testdisk or Windows tools.

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Testdisk also can create a new BS, but it used to be the XP type. You then have to run chkdsk from a newer copy of Windows which will convert it to the newer version.

If for example, you installed grub to sda1, it will overwrite the Windows PBR. Testdisk may say it is valid as grub can be in a PBR (but never should be), just not in any Windows formatted partitions.

---

### Post by arius88 on 2023-04-24
Always good to hear back from you, Fred. 

Ran chkdsk from the Windows 7 install disk. No errors, so I'm guessing the PBR is okay.
Going to take a nap and then see what I can do with Testdisk.

---

### Post by oldfred on 2023-04-24
If PBR - partition boot sector is not seen as NTFS, chkdsk does not run.
Depending on which parameters you used, you may have repaired it.

---

### Post by arius88 on 2023-04-24
Okay!

Ran testdisk. All went according to plan (for once, finally)! :guitar:
Refreshed the devices and the little yellow warning triangle of doom is gone and sda 1 is flagged as boot. Excellent.

Should I run boot-repair now?

Follow up question: do I run it off the live gparted install... or how does that work? I typed "boot-repair" into a terminal there and it said "command not found."

---

### Post by arius88 on 2023-04-24
oops posted that last one twice by mistake

---

### Post by oldfred on 2023-04-24
Boot-Repair is not a standard Ubuntu application. And live installers do not save changes, unless you created one with persistence and saved it.

You just need to add ppa again to reinstall it each time you reboot with live installer. If in your install then you can just run it.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by arius88 on 2023-04-25
Quick follow up question: do i need to run boot-repair from a live cd, or can I just run it from within Lubuntu?

Update: the Boot-Repair article says I can run it from within my Lubuntu install, so that's what I'm trying right now. (Sorry for asking an unnecessary question.) Will post here if it works (or not).

---

### Post by arius88 on 2023-04-25
Ran Boot-Repair. It didn't work. The pastebin is here: [https://paste.ubuntu.com/p/fXr8JNCmMn/](https://paste.ubuntu.com/p/fXr8JNCmMn/)

Boot menu contains two options for Windows 7.

Selecting Windows 7 (on /dev/sda1) takes me to a blinking curser.
Selecting Windows 7 (on /dev/sda2) takes me to the same error that started all this: 

"Windows failed to start. A recent hardware or software change might be the cause.

"Status: 0xc0000225

"Info: The boot selection failed because a required device is inaccessible."

:(

Dang. What do I do now?

---

### Post by oldfred on 2023-04-25
Do not remember if it was Windows 7 that would get you into an internal repair console with f key like f10? You had to hit that before it starts to boot, but after starting Windows.
Grub only boots working Windows.

The real disadvantage of BIOS/MBR installs is you only have one MBR with boot files. Grub boots working Windows, but to make Windows repairs you often have to directly boot Windows and then need a Windows boot loader in MBR.
You then use Windows repair flash drive or install Windows boot loader (or maybe Boot-Repair & generic (syslinux) boot Windows & make Windows repairs. Then restore grub to dual boot.

Boot-Repair copied bootmgr & BCD which are the essential boot files in sda1 Windows boot partition to main install sda2. That is now why grub gives two boot options. But files were copied, so boot errors should be the same?
Did you run chkdsk on both sda1 & sda2?

---

### Post by arius88 on 2023-04-25
TBH I don't remember what I ran chkdsk on. I thought it checked all the partitions, but I can do it again to confirm.

Is there a way to get a Windows boot loader in the MBR?

---

### Post by oldfred on 2023-04-25
See post #5.
Either Boot-Repair or your windows repair/recovery flash drive.

---

### Post by arius88 on 2023-04-25
Thing is that running boot-repair is the most recent thing I did that would have made any changes, and it didn't fix it. And apparently I don't have a windows disk that will do the job either.

I had downloaded a Windows 7 disk. It comes with an option to either install or repair windows. I've been selecting the repair option. It gives me a System Recovery Options screen. There's two options there.

The second option is no use to me, because it involves restoring the computer with a system image I never created.

The first option is "Use recovery tools that can help fix problems starting Windows. Select an operating system to repair." It would then show me a blank window with no operating systems. It suggested to load drivers, which I don't have and didn't know how to do. Since making some recent changes, either with Gparted or boot-repair, it seems we've made some progress because Windows 7 now shows up in the window! When I click on Next, it detects something wrong and offers to fix it, but then I get an error:

"This version of System Recovery Options is not compatible with the version of Windows you are trying to repair. Try using a recovery disc that is compatible with this version of Windows." 

Any idea where I might acquire such a thing? 

NeoSmart sells a Windows 7 Professional recovery disk for $59.99 here: [https://neosmart.net/EasyRE/#buy](https://neosmart.net/EasyRE/#buy), but I'm hesitant to drop money on something if I don't even know if it will work. And I also don't particularly trust this website, although it WAS recommended here: [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)

---

### Post by oldfred on 2023-04-25
Are you using Boot-Repair's advanced mode? And choose Windows & sda?
That should install the generic (syslinux) boot loader).
But that will not make any other Windows repairs.

Windows 7 is so obsolete, I would not spend any money on it.
There used to be a free Windows 7 repair disk. Maybe 15 years ago, I used it to fix my XP install, it ran a better chkdsk than XP.
And you could make your own repair disk from with a Working Windows.
A newer Windows repair disk may work?

Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive) & 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by arius88 on 2023-04-25
I haven't been using Boot-Repair's advanced mode! Just clicking that Recommended Repair button. TBH I have no idea how to use advanced mode. It looks confusing. When I go here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) is says this under Advanced options:

[B]Warning:  the default settings are the ones used by the "Recommended Repair".  Changing them in the Advanced options may worsen your problem. Don't  change them unless requested by experienced helpers. 
[/B]

It's not so much Windows 7 that I would be spending money on as the $1000 of software installed on there. But you make a good point and I would definitely consider that a last resort. 

Thank you for all the links! I might try a newer repair disk later, but let's see if I can figure out this advanced mode Boot-Repair thing first before I go that route.

---

### Post by arius88 on 2023-04-25
Before I make a horrible mistake, just want to confirm. Am in the Advanced options now. Under the "GRUB location" tab, it says: OS to boot by default. It was listing sda4. There are two other options aside from sda4.  One is "sda1: Windows 7 (boot) (via sda4 menu)" and the other is "sda2: Windows 7 (via sda4 menu)." I assume I want to boot sda1?

Under the "Main Options" tab, there are unselected options to Restore MBR and to Repair file systems. I'm wondering if I should select those as well.

---

### Post by oldfred on 2023-04-25
Never used Boot-Repair to restore MBR, as have used UEFI for years.
So all I can do is read instructions also.

Boot-Repairs normal fix is to reinstall grub for first Linux install it sees.
Advanced mode then lets you choose an install and choose a drive.

Always choose drive to install boot loader into like sda, never a partition like sda1.

---

### Post by yancek on 2023-04-26
The error you are reporting may mean you downloaded the wrong version, home, profession, pro, whatever so take a look at the link in my post above which has several links to different sites.  One of them is to the microsoft site which I would try first.

Neosmart is reliable and I've used EasyBCD on windows 7 successfully.  I've just been reviewing there site and I no longer see an option for a free download but there is other software available which costs less that $59.  Hopefully, boot repair will help but as pointed out above, if your windows boot files are corrupted, it won't help as Grub simply chainloads windows and does not directly boot it.  That means it points to the specific sector where PBR files are located and if they are missing or corrupt, Grub won't boot window.  EasyBCD has an Advaned Settings option which may help but I've only used it to add a Linux entry to the BCD menu so not sure what that option does.

[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

The site at the link below has a free download of EasyBCD.  I'm not familiar with the site so don' know how reliable it is.

[https://www.techspot.com/downloads/3112-easybcd.html](https://www.techspot.com/downloads/3112-easybcd.html)

---

### Post by arius88 on 2023-04-26
That's all very helpful, thank you both!

I will give EasyBCD a shot and report back. (Really appreciate that link, Yancek.)

---

### Post by arius88 on 2023-04-26
Turns out EasyBCD is a DOS-based executable file that only works in Windows. Not super useful to me right now since I can't get Windows to boot. 
However, I'm wondering if it would make sense to set up Wine (never used it before, but have been curious to try) on Lubuntu and then run EasyBCD off that?

In the meantime I'll try the Windows site.

Update: tried Yancek's windows link for the third time. Can't find anything helpful on the site. Searching for a Windows 7 Recovery Disk just takes me to a page with advice on how to upgrade to a newer version of Windows. Gonna look into getting a system recovery disk some other way. Fred had suggested that using a newer disk might work.

---

### Post by arius88 on 2023-04-26
Based on an earlier Fred suggestion, I might also give this a shot if I get Wine up and running: [https://www.tenforums.com/software-apps/117664-win10xpe-build-your-own-rescue-media.html](https://www.tenforums.com/software-apps/117664-win10xpe-build-your-own-rescue-media.html)

---

### Post by arius88 on 2023-04-27
Update: I've abandoned all hope of ever making WINE work. It won't show up in any menus, it won't launch anything from command line, I've been fighting with it for hours and getting nothing but error messages.

Quick Q: Can I run EasyBCD.exe in virtualbox? 

(ie, can I make changes to the BIOS [or whatever it needs to do to fix it so Windows will boot again] from within a virtual machine?)
I have never used a virtual machine before but I downloaded virtualbox and am willing to put some time into figuring it out if it's at all feasible.

---

### Post by yancek on 2023-04-28
I thought it might be possible to run EasyBCD from a bootable DVD or USB but it isn't possible,  That's surprising but the way it is.  

To use EasyBCD in a virtual machine, you would need to have windows installed in the virtual machine.  That won't help to repair your current problem.

---

### Post by arius88 on 2023-04-30
Okay, I tried switching the boot flag over to sda2. That had no effect at all.

It seems we've reached the end of the road in terms of viable ideas. I'm going to try bringing in a professional.

Really want to thank you two for the help - especially you, Fred. You've been relentlessly supportive and it was nice to not have to go through this alone.

---

### Post by arius88 on 2023-04-30
Just came back to say - my computer tech friend was able to fix it! I can't explain how relieved I am. Not sure what he did, but he was able to resolve it with the Windows disk I had.  Again, thank you - I really appreciated the support.

---

