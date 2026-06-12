---
title: "After removing Xubuntu 14.04, Windows 7 no longer boots, broken WUBI detected"
date: 2016-07-06
forum: Windows
---

### Post by marcinoo on 2016-07-06
Hello,

I'm not sure if this is a correct forum section to place it, if not  please move the thread. Also sorry for my crappy english slang, but I'm  not a natively english. My Win7 is broken and unbootable, I already  spent 2 days to fix it, but with no success. I'm already writing my post  from Rescatux rescue CD, which has an internet browser built-in (almost  unsuable btw. I'm happy that I even could get to register on the  forums). Now the dramatic horror story...

I had a working dual-boot Windows 7 64bit UEFI GPT + WUBI Xubuntu 14.04  UEFI 64bit over it, for some time (installed as a standalone application  under Windows 7 on the Windows 7 partition), but two days ago I decided  to remove Xubuntu from my computer, so I booted to Windows 7 and  entered into Add/Remove Programs panel and clicked on uninstall Wubi  Xubuntu, but that did not want to uninstall  - just a some window  appeared + a rotating circle (of a mouse cursor), like something is  being uninstalled and going on, but after several seconds the window and  the circle have disappeared, and Xubuntu still has not been uninstalled  and still was visible in Add/Remove programs and Xubuntu folder was  still existing on HDD, no confirmation like "uninstall successfull or  "error", just nothing. So I had repeat the uninstallation several times  but every time the same thing happens, the just refuse to uninstall  with no kind of a feeback. So as it was unable to uninstall itself...I  helped it a bit to do so by removing Xubuntu folder manually from the   Windows 7 partition, and then I rebooted the computer... and there is  where the problem begins.. I can no longer boot Windows 7, some error  appeared - white font on black screen:

>  Minimal bash-like line editing is supported for the first word  tab list possible command completions. Anywhere else TAB lists possible  device od file.

grub> _


So I started to google and tried various solutions found on various forums:

- booting Windows 7 ISO, use "Fix boot" and then restarting the computer, but that didn't help, so I continued:

- booting Windows 7 ISO and entering the command line "bootrec / fixmbr"  and then "bootrec / fixboot" - in both cases I received feedback:

> Result: The operation completed successfully

and then restarting the computer, but that didn't help too, so I continued:

- booting Windows 7 ISO and entering the command line "bootsect / nt60  C:" and then restarting the computer, but that didn't help too, so I  continued:

- booting Windows 7 ISO and entering the command line "bootsect /  nt60all / mbr" and then restarting the computer, but that didn't help  too, so I continued:

- booting Windows 7 ISO and entering the command lines:

> 
diskpart
list disk
select disk (I choosed Windows 7 disk)
list partition
select partition (I choosed Windows 7 partition)
detail partition (it was unactive, so)
active

but I received a feedback:

> The selected disk is not a fixed MBR disk. Only on fixed MBR disks it's possible to mark a disk as active.
so I continued:

- booting Windows 7 ISO and entering the command line "bootsect /rebuildbcd" - I received a feedback:
about unable to locate my Windows 7 installation and something about  partition being locked (I don't remember exactly the "locked" message):

> The drive where Windows is installed is locked.
"Successfully scanned Windows installations.
Total identified Windows installations: 0
The operation was completed successfully."

and then restarting the computer, but that didn't help too


Meanwhile during subsequent boot tries the above-mentioned commands in  all the above mentioned ways, Windows 7 still does not get up and just  changed error messages:

> Insert a boot disk and press any key

> Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key

> No partition is active

and finally I'm stuck with:

> Missing operating system

So finally I downloaded and booted from:

> Rescatux Rescue CD [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

which just serves to fix such problems with booting and I chosed "Repair" however instead fix, Rescatux told me to use:

> Boot Rescue Disk 64bit" [https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

so I did so, downloaded, booted and chosed "Repair" and then restarted  the computer, but that didn't help too , however that generated a  usefull log:

> [http://paste.ubuntu.com/18521712](http://paste.ubuntu.com/18521712)

another log:

> [http://paste.ubuntu.com/18519581](http://paste.ubuntu.com/18519581)

So I posted my problem on:

> [http://ubuntu.pl/forum/viewtopic.php?f=133&t=180033](http://ubuntu.pl/forum/viewtopic.php?f=133&t=180033)

But the guys were unable to help me, so I decided to post here.

Meanwhile I also removed some 2 files from Windows 7 partition,  something like wubildr.efi + another one but that didn't help too. I  also realised myself that all the bootrec /fixmbr like commands are not  applicable for GPT.

My Windows 7 is completely unbootable now. I also still have Xubuntu  entry in BIOS and also in BIOS boot list (when pressing F12). When I'm  booting Xubuntu from the inside of BIOS, a black screen appears for 1  second, and it gets back to BIOS. I guess that's because it fails to  find Xubuntu on Windows 7 partition because Xubuntu has been removed.  When I'm booting Xubuntu from outside the BIOS, from BIOS boot list  (when press F12), a mainboard logo appears for 10 seconds and then an  error appears "Missing operating system" but I suppose the error message  in this case is not because of booting Xubuntu, but because of  alternatively booting a Windows 7 HDD as NONUEFI (PO SAMSUNG EVO 850  120GB) which is a second boot option after Xubuntu, I mean after Xubuntu  fails to load, it tries to load the second option which gives the  error. So Xubuntu boot gives black screen + return. The third boot  option is UEFI Samsung 850 EVO 120GB which used to successfully boot  Windows 7, before all got broken, but now it gives "Missing operating  system" too.

At the end of logs there is:

> A broken Wubi has been detected. Please fix it this way:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

As for the log: sda is my main OS internal hdd with the dual-boot,  Windows 7 partition is sda3, sdb is just my external repair usb hdd with  boot repair images ( I'm already booted from it to Rescatux)

Please help me to fix broken WUBI, clean Xubuntu entries from BIOS, and bring back Windows 7 working.

edited:

This is the uninstall which has not worked for me and I was talking about in beginning of the post:

> [https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F)

And this is what I had already do:

> [https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

I had removed C:\xubuntu folder and C:\wubildr* files from Windows 7 partition and I also removed Ubuntu folder with EFI files from 100MB EFI FAT32 partition, so now the log says:

> 
Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 

instead of

> 
Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/ubuntu/wubildr/MokManager.efi 
                       /EFI/ubuntu/wubildr/grubia32.efi 
                       /EFI/ubuntu/wubildr/grubx64.efi 
                       /EFI/ubuntu/wubildr/shimx64.efi

I also tried booting Windows 7 ISO and entering the command line* bcdedit* to list the boot entries and then to use *bcdedit /delete {GUID}*, but when I entered *bcdedit *I got 2 only 2 Wndows Bot Entries: Windows Bot Manager and Windows Bot Loader, something like that:

> Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=V:
path                    \bootmgr
description             Windows Boot Manager
locale                  en-US
default                 {e58e9c4c-dc5b-11e1-be69-bb3b6bb64ef4}
displayorder            {e58e9c4c-dc5b-11e1-be69-bb3b6bb64ef4}
bootsequence            {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 3

Windows Boot Loader
-------------------
identifier              {e58e9c4c-dc5b-11e1-be69-bb3b6bb64ef4}
device                  partition=C:
path                    \WINDOWS\system32\winload.exe
description             Windows 7 Ultimate (recovered) 
locale                  en-US
recoverysequence        {e58e9c4d-dc5b-11e1-be69-bb3b6bb64ef4}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \WINDOWS

thus no Ubuntu entry to delete, it seems it already has been deleted.

So what I want to say is that I have purged all Wubi-Xubuntu files from whole HDD, and the only & last thing which left is the Xubuntu entry in BIOS and in BIOS boot menu which point to unexisting Xubuntu, and which should be replaced back with Windows 7 entry.

I had try to boot into[SIZE=2]:
> The rEFInd Boot Manager[/SIZE]> 
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)[URL="http://sourceforge.net/projects/refind/files/0.10.3/refind-cd-0.10.3.zip/download"] 
http://sourceforge.net/projects/refind/files/0.10.3/refind-cd-0.10.3.zip/download[/URL]

to manage UEFI BIOS boot entries but can't boot this CD due to an error:

> Error 13:([http://grub4dos.chenall.net/e/13](http://grub4dos.chenall.net/e/13))
Invalid or unsupported executable format

I also tried - booting Windows 7 ISO and entering the command line "chkdsk c: /r /f " but gets an error:

> 
The type of the file system is NTFS
Cannot lock current drive.


 Chkdsk cannot run because the volume is in use by another process. 
Chkdsk may run if this volume is dismounted first. 
ALL OPENED HANDLES TO  THIS WOULD THEN BE INVALID.
Would you like to force a dismount on this  volume? <Y/N> N

Chkdsk cannot run because the volume is in use by another process. 
Would you like to schelude this volume to be checked the next time the system restarts? <Y/N> N



I remember that 2 months ago I tried chkdsk to fix my external usb hdd the same way and I answered Y, and that broken the hdd completely and made it unaccessible, no partition / file recovery tool was able to access nor recover any partition / file from it, it was completely unaccessible, my luck I had a backup of all the lost files. I had to remove all partitions from that hdd and make new ones to make the hdd working again. I do not recommends answer Y until you are sure what you are doing...

---

### Post by oldfred on 2016-07-06
You have UEFI on sda with gpt partitioning. 

But have sdb as MBR(msdos) partitioning. Generally better with UEFI systems to have all drives as gpt, but not required.

And then it looks like you installed wubi into a partition on the MBR drive? Or did you follow the directions to install to gpt which is more complicated than a full install of Ubuntu? One of the main issues with wubi was it did not work with gpt partitions which new UEFI systems have.

And you managed to install BIOS boot loader for Windows on the UEFI boot drive. You still look like if you turn on UEFI boot and choose the Windows UEFI boot option in UEFI you should be able to boot Windows. The BIOS boot of Windows will never work, but does not have to be erased in MBR.

Reboot Boot-Repair in UEFI mode. And make sure UEFI Secure boot is off in UEFI settings.
Rerun Boot-Repair.
Since your system is UEFI, be sure to always boot system in UEFI boot mode and flash drives in UEFI boot mode. 

You need to remove /efi/ubuntu folder in ESP - efi system partition or your sda1 partition.

You never want the BIOS purple boot screen:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

This is more about deleting Windows UEFI entries, but same instructions apply to any UEFI entry.

 [http://askubuntu.com/questions/794725/can-i-remove-windows-boot-manager-from-dedicated-ubuntu-computer/795341#795341](http://askubuntu.com/questions/794725/can-i-remove-windows-boot-manager-from-dedicated-ubuntu-computer/795341#795341)

---

### Post by marcinoo on 2016-07-06
Hello,
thanks for reply, I updated and edited my post just right now, probably at the same time you were posting your post, thus you probably missed the updated part - it beigins with "edited".

As for the sdb as I already wrote, don't worry about it, it is completely not important, as the sdb is just my external usb hdd for backup & repair purposes only, it is unplugged and tucked away in the closet most of the time and also was so when installing Xubuntu (until now). 

I have installed WUBI on Windows 7 HDD GPT.

I have Secure Boot Off.

As in the post update, I already removed /efi/ubuntu folder in ESP - efi system partition on my sda1 partition.

As for the sudo efibootmgr -v It throws an error:

> Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.

When I try "sudo modprobe efivars", nothing happens.

I'm currently on PartedMagic 2013_08_01 (the latest pay-free) booted from the external hdd.

When I boot into Boot_Repair_Disk64, and try [OS-Uninstaller]("https://sourceforge.net/p/os-uninstaller/wiki/"), it says no OS found.

---

### Post by oldfred on 2016-07-06
You need to be sure to boot in UEFI mode.
Have not recently booted parted magic, suggest using Ubuntu live installer 16.04 and add Boot-Repair. If in UEFI mode then you should be able to see and work on UEFI settings.

From your BIOS boot you still should be able to see the /EFI/ubuntu folder in the ESP and delete it.

---

### Post by marcinoo on 2016-07-07
Yes I DID run Boot-Repair-Disk64 in UEFI mode X times already, I clicks REPAIR-BOOT,  Boot-Repair window appears, it takes several minutes to complete and at the end it says:

> Boot successfully repaired.

A new file (~/Boot-Info_2016_-07-07__09h03.txt) will open in your text viewer.

In case you still experience boot problem , indicate its content to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.

But the txt file does not opens in the text viewer. 
Nothing happens.
So I just reboots my computer but it is not repaired.
And as the txt log file did not open in the text viewer I had to generate an internet log by running Boot-Repair-Disk64 again and selecting Generate Boot-Repair Info, and this is the log:

> [http://paste.ubuntu.com/18690246/](http://paste.ubuntu.com/18690246/)

I'm not sure but does from the log seems it tries to repair my external bootable E2B USB drive, which I booted into Boot-Repair-Disk64 from? Instead of repairing my internal system Windows 7 hdd, which is broken and is the one which should be repaired...

> [http://www.easy2boot.com/make-an-easy2boot-usb-drive/make-and-e2b-usb-drive-using-rmprepusb/](http://www.easy2boot.com/make-an-easy2boot-usb-drive/make-and-e2b-usb-drive-using-rmprepusb/)

It even don't ask me or let me choose which disk to repair

If I boots to Boot-Repair-Disk64 from the external hdd, and then unplug the external hdd, and then beings  Boot_Repair, it still does not repairs my Win7 hdd , even if it says repaired successfully and I do reboot.

As for the OS-Uninstaller, it now runs, but it tries to remove Widows 7,  seems it can not delete OS from bios, only from disk, but there is no Xubuntu on the disk anymore, so it tries to delete Windows 7. I had read somewhere on internet that it is able to delete OS from BIOS But it seems it is not such kind of tool.

I'm tired of all that ****. I already spent 3 days on some liveCDs trying to fix my broken Win 7 PC as homeless under a bridge without housing

How much ugly and nasty software is WUBI that could blow up Win7, and nothing is able to fix what WUBI did.\

What people craete such kind of ****.

The whole Linux Desktop is also ****.

I just wanted to Uninstall Wubi-Xubuntu and get back  to Win7, but no....WUBI won't let me go free, it must blow up everything in its path before it can get removed.

Are here any authors of WUBI ? 

You create such crap, now help me to get rid of it (from the BIOS) , please. (and I know it is not officialy supported anymore)

---

### Post by oldfred on 2016-07-07
This is a forum of users helping other users. We rarely if ever see developers of software.

And now that wubi has been obsolete for so long, few users that even know or use wubi are available.
There may be one user who for his own knowledge modified Wubi to work with UEFI & gpt. But now it is more complicated than a full install, so not the original intent of wubi of making it easy to install in a BIOS based Windows system.
Trying to force BIOS based software into an UEFI system whether Linux or Windows will lead to failure.

Your latest summary report is not showing any wubi files?

And you deleted your partitions on sdb, and created a new FAT32 partition. Generally we suggest FAT32 only for smaller partitions as it cannot store large files and has no journal to make repairs easier or possible. Use NTFS.

You now show Clover & Easy2Boot, I know nothing about them.

Found this on Clover, but it is intended for BIOS based systems. You may want to look into rEFInd which is for UEFI based systems.
> This is EFI-based bootloader for BIOS-based computers created as a replacement to EDK2/Duet bootloader [http://www.tianocore.org](http://www.tianocore.org)

---

### Post by marcinoo on 2016-07-07
Hello

> **oldfred said:**
> Your latest summary report is not showing any wubi files?

Because as already I wrote earlier in my 1st post in this thread, I already removed all Wubi-Xubuntu related files:

> **marcinoo]So what I want to say is that I have purged all Wubi-Xubuntu files from  whole HDD, and the only & last thing which left is the Xubuntu entry  in BIOS and in BIOS boot menu which point to unexisting Xubuntu, and  which should be replaced back with Windows 7 entry.[/quote]


[QUOTE=oldfred said:**
> And you deleted your partitions on sdb, and created a new FAT32 partition. Generally we suggest FAT32 only for smaller partitions as it cannot store large files and has no journal to make repairs easier or possible. Use NTFS.

I did not delete any partitions from my external E2B usb hdd, I just switched  my external E2B usb hdd to UEFI mode to be able to boot Boot-Disk-Repair64 in UEFI mode. IN this case E2B 'switch' partitions from LEGACY to UEFI mode:
> [http://www.easy2boot.com/add-payload-files/adding-uefi-images/](http://www.easy2boot.com/add-payload-files/adding-uefi-images/)


> **oldfred said:**
> You now show Clover & Easy2Boot, I know nothing about them.

You don't need to know anything about it, why would you want to know something about it? 
The thread is all about the internal Hdd with broken Windows 7.
E2B is just a powerfull tool to boot multiple ISO images from USB Pendrives or USB external HDDs
> [http://www.easy2boot.com/](http://www.easy2boot.com/)
I use it to diagnose & repair my PC, I boots into some Live Linux Distros or WinPE to be able to do repairs, manage partitions, post on forums...It is just visible in logs but has nothing common with broken Windows 7 internal hdd. Just do not worry about it

> **oldfred said:**
> Found this on Clover, but it is intended for BIOS based systems. You may want to look into rEFInd which is for UEFI based systems.

I already tried and I wrote about it in my first post...did you ever read my posts...
It throws an error when booting:

> Error 13:sad:[http://grub4dos.chenall.net/e/13](http://grub4dos.chenall.net/e/13))
Invalid or unsupported executable format

Maybe because I did not boot it in UEFI mode, I'll try later again.

And also E2B also has UEFI support.

OK.

I live-booted Ubuntu 16.04 in UEFI mode and efibootmgr works out of the box, (it was broken on PartedMagic, maybe because I had not boot PartedMagic in UEFI mode, I don't know),
I removed Xubuntu entry from BIOS & BIOS boot list (it was pointing to EFI/Ubuntu)
I added 4 Windows entries because I don't know which efi file I should boot to,
ubuntu@ubuntu:~$ sudo efibootmgr -v output:
> **sudo efibootmgr -v output]
BootCurrent: 0006
Timeout: 10 seconds
BootOrder: 0000,0001,0004,0005,0006,0002
Boot0000* UEFI: Windows bootx64.efi    HD(1,GPT,2ea5fdfe-f040-43e8-b216-72690571ca2e,0x800,0x32000)/File(\EFI\Boot\bootx64.efi)
Boot0001* UEFI: Windows bootmgfw.efi    HD(1,GPT,2ea5fdfe-f040-43e8-b216-72690571ca2e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot0002* Hard Drive     BBS(HD,,0x0)AMGOAMNO........o.S.a.m.s.u.n.g. .S.S.D. .8.5.0. .E.V.O. .1.2.0.G.B....................A...........................>..Gd-. said:**
> 

Boot0002* is PO SAMSUNG 850 EVO 120GB (LEGACY entry) which throws "Missing operating system"
Boot0006* is live-booted Ubuntu 16.04 from my E2B usb hdd


But no one of them works, Windows 7 does not boot
I boot my PC, I press F12, boot menu appears, no matter which one Windows entry I boot (also when I choose UEFI Samsung EVO 850 120 GB), it just shows my motherboard's logo and after timeout (10s)  is out **IT BOOTS NEXT DEVICE** instead of Windows 7, (for ex My internal usb HDD or PO SAMSUNG 850 EVO 120GB which gives "Missing operating system" (as it is a NON UEFI boot entry I think).

(And above there is no UEFI Samsung EVO 850 120 GB listed currently because my Samsung EVO is hardware encrypted with opal password, and the entry only appears after I shutdown PC, after I turn on my PC, I choose then UEFI Samsung 850 EVO 120GB boot and it asks me for the password, once I enter the password the drive is unlocked, PC reboots, and since now the entry is gone and now I have to select Linux or Windows boot entry to boot in the OS. yes it requires to restart my PC again but only if Pc has been turned off. It does not affect reboots/restarts.

> [https://github.com/Drive-Trust-Alliance/sedutil](https://github.com/Drive-Trust-Alliance/sedutil) )

Why do the Windows entries (and the old Xubuntu entry) boots to NEXT DEVICE?

Damn, and what the hell is that:
[quote][https://github.com/Drive-Trust-Alliance/sedutil/issues/66](https://github.com/Drive-Trust-Alliance/sedutil/issues/66)

---

### Post by oldfred on 2016-07-07
Windows uses this as its UEFI boot file:
 \EFI\Microsoft\Boot\bootmgfw.efi

And this is the fallback or hard drive boot file. Windows installer, Ubuntu installer or any external device uses this filename as the UEFI standard to boot. Newer UEFI can use it also on internal drives.
\EFI\Boot\bootx64.efi 

If your UEFI has a setting saying "Windows" or "Other" you have to use "Other" with Windows 7. 
That really is the UEFI Secure Boot setting and Windows 7 does not support Secure Boot.

If Windows still does not boot it probably needs Windows repairs. Use f8 or your Windows repair disk and its repair console.
      
 f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

---

### Post by marcinoo on 2016-07-07
> **oldfred said:**
> 
If your UEFI has a setting saying "Windows" or "Other" you have to use "Other" with Windows 7. 
That really is the UEFI Secure Boot setting and Windows 7 does not support Secure Boot.

It already is so set (on "other")
And Secure Boot also is already disabled.

> **oldfred said:**
> If Windows still does not boot it probably needs Windows repairs. Use f8 or your Windows repair disk and its repair console.

I already tried Windows repair disk and repair console and it didn't work as I already wrote in 1st post.
 I'll try F8 yet.

---

### Post by hakuna_matata on 2016-07-07
If the Wubi uninstaller doesn't delete anything, it is not really a problem.

I assume you used one of the first versions with UEFI patches that could be locked if the EFI partition is mounted by another program. It always logs the reason in %temp%. %temp% should be a short cut for your temporary folder path e.g. **C:\Users\YourUserName\Local\Temp** . file name is e.g.: **wubi-14.04-rev286.log**

If you unmount the EFI partition or if you reboot Windows to get an unmounted EFI partition, it should work. 

It is also possible to remove it manually. If you are in UEFI mode you can use

```
bcdedit /enum firmware

```
or
```
bcdedit /enum all

```

Then you can delete the Ubuntu (or Xubuntu in your case) entry with the shown {GUID}.

Be sure that the entry with {bootmgr} is the entry for Windows with
```
path                    \EFI\Microsoft\Boot\bootmgfw.efi

```
Do NOT delete this entry. Windows needs this entry to boot in UEFI mode. It is not enough to create an entry with efibootmgr.

I assume that you overwrote this entry by repairing it with Windows 7 ISO in BIOS mode.

On my experience the easiest way to get a working BCD for Windows with Ubuntu ISOs if you restore a backup of BCD file to **/EFI/Microsoft/Boot/BCD** on EFI partition.
Maybe, you created a backup with programs like [EasyBCD]("https://neosmart.net/EasyBCD/") (folder **/Users/YourUserName/Documents**) in the past.

---

### Post by marcinoo on 2016-07-07
Hello

> **hakuna_matata said:**
> If the Wubi uninstaller doesn't delete anything, it is not really a problem.

I assume you used one of the first versions with UEFI patches that could be locked if the EFI partition is mounted by another program. It always logs the reason in %temp%. %temp% should be a short cut for your temporary folder path e.g. **C:\Users\YourUserName\Local\Temp** . file name is e.g.: [B]wubi-14.04-rev286.log
[/B]

After your post I searched my Windows 7 partition and indeed, lots of usefull wubi log and config files remains have been found, mainly in temp directory:

> [https://i.imgsafe.org/eb29743327.png](https://i.imgsafe.org/eb29743327.png)

I compressed all the files and uploaded:

> [http://s000.tinyupload.com/index.php?file_id=28131386633262936024](http://s000.tinyupload.com/index.php?file_id=28131386633262936024)

My TEMP dir is almost 400 files and takes 630mb of space, feel free to ask for any additional files I missed'n you needs.

> **hakuna_matata said:**
> 
If you unmount the EFI partition or if you reboot Windows to get an unmounted EFI partition, it should work. 

I don't know what mean "unmount EFI partition"

> **hakuna_matata said:**
> 
It is also possible to remove it manually. If you are in UEFI mode you can use

```
bcdedit /enum firmware

```
or
```
bcdedit /enum all

```

Then you can delete the Ubuntu (or Xubuntu in your case) entry with the shown {GUID}.

Be sure that the entry with {bootmgr} is the entry for Windows with
```
path                    \EFI\Microsoft\Boot\bootmgfw.efi

```
Do NOT delete this entry. Windows needs this entry to boot in UEFI mode. It is not enough to create an entry with efibootmgr.

I already mentioned about that in my 1st post, pllease read about it in the 1st post - (press F3 in internet browser and search for "bcdedit" to jump quickly to that part of the post). In brief, it haven't found any Xubuntu entries, and it found some Windows entries. Are they correct?

> **hakuna_matata said:**
> 
I assume that you overwrote this entry by repairing it with Windows 7 ISO in BIOS mode.

Maybe, I don't have a clue.

> **hakuna_matata said:**
> 
On my experience the easiest way to get a working BCD for Windows with Ubuntu ISOs if you restore a backup of BCD file to **/EFI/Microsoft/Boot/BCD** on EFI partition.
Maybe, you created a backup with programs like [EasyBCD]("https://neosmart.net/EasyBCD/") (folder **/Users/YourUserName/Documents**) in the past.

Unfortunately not.

---

### Post by hakuna_matata on 2016-07-07
> ```
07-04 16:46 DEBUG  WindowsBackend: command >>C:\Users\user\AppData\Local\Temp\pylD4EA.tmp\bin\7z.exe l D:\sys.iso
07-04 16:46 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-04 16:46 DEBUG  Distro:   checking Ubuntu ISO D:\sys.iso
07-04 16:46 ERROR  root: iteration over non-sequence
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\backends\common\backend.py", line 190, in fetch_basic_info
  File "\lib\wubi\backends\common\backend.py", line 803, in find_any_iso
  File "\lib\wubi\backends\common\distro.py", line 113, in is_valid_iso
TypeError: iteration over non-sequence
```
I found the reason for the issue of the uninstaller. There was a mismatched iso on D:\ It's name is sys.iso. If you rename or remove that file, the uninstaller would work.The issue was reported for installation and I fixed it with rev.308 (see [here]("https://github.com/hakuna-m/wubiuefi/issues/9")) but I didn't know that it also affects the part for uninstalling.

But IMHO it is not the reason why your BCD is mismatched.
> I already mentioned about that in my 1st post, pllease read about it in  the 1st post - (press F3 in internet browser and search for "bcdedit" to  jump quickly to that part of the post). In brief, it haven't found any  Xubuntu entries, and it found some Windows entries. Are they correct?

No, they are not correct for UEFI mode. That is the reason why I wrote "I assume that you overwrote this entry by repairing it with Windows 7 ISO in BIOS mode." It should be like [URL="https://msdn.microsoft.com/en-en/library/dn336950.aspx"]that

[/URL]Can you try to rebuild your BCD for UEFI mode?

---

### Post by marcinoo on 2016-07-08
Hey

it was me who was reporting the issue with the sys.iso file,, I renamed the sys.iso to sys.ixo temporarily to get WUBI install working, but after I installed Xubuntu with WUBI successfully, I renamed sys.ixo back to sys.iso. and just like you I didn't know that it also affects the part for uninstalling...

As for the bcdedit, one more thing yet, a small correction: I forgot that the bcd entries from the 1st post are not exactly my bcd entries , they are just similiar, they are just  examples.
I'll boot into Windows 7 iso Repair Console and I'll post my real bcd entries in a moment.

Ok I'm back and here are my real BCD entries: (more than 2 entries because this is an output from "bcdedit /enum all" instead of "bcdedit" (which oputput only 2 entries like in my 1st post)):
> 
Firmware Boot Manager 
--------------------- 
identifier              {fwbootmgr} 
displayorder            {bootmgr} 
                        {17a8052c-1f41-11e6-bd45-902b346f5367} 
                        {4c72f739-4528-19e6-b781-806e6f6e6963} 
                        {4c72f73a-4528-19e6-b781-806e6f6e6963} 
                        {4c72f73b-4528-19e6-b781-806e6f6e6963} 
                        {4c72f73c-4528-19e6-b781-806e6f6e6963} 
                        {4c72f73d-4528-19e6-b781-806e6f6e6963} 
                        {b650944c-0267-11e6-92b6-806e6f6e6963} 
timeout                 10 
 
Windows Boot Manager 
-------------------- 
identifier              {17a8052c-1f41-11e6-bd45-902b346f5367} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\ubuntu\wubildr\shimx64.efi 
description             Xubuntu 
locale                  pl-PL 
inherit                 {globalsettings} 
default                 {default} 
displayorder            {default} 
toolsdisplayorder       {memdiag} 
timeout                 30 
 
Windows Boot Manager 
-------------------- 
identifier              {bootmgr} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\Microsoft\Boot\bootmgfw.efi 
description             Windows Boot Manager 
locale                  pl-PL 
inherit                 {globalsettings} 
default                 {default} 
displayorder            {default} 
toolsdisplayorder       {memdiag} 
timeout                 30 
 
Firmware Application (101fffff) 
------------------------------- 
identifier              {4c72f739-4528-19e6-b781-806e6f6e6963} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\Boot\bootx64.efi 
description             UEFI: Windows bootx64.efi 
 
Firmware Application (101fffff) 
------------------------------- 
identifier              {4c72f73a-4528-19e6-b781-806e6f6e6963} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\Microsoft\Boot\bootmgfw.efi 
description             UEFI: Windows bootmgfw.efi 
 
Firmware Application (101fffff) 
------------------------------- 
identifier              {4c72f73b-4528-19e6-b781-806e6f6e6963} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\Microsoft\Boot\bootmgr.efi 
description             UEFI: Windows bootmgr.efi 
 
Firmware Application (101fffff) 
------------------------------- 
identifier              {4c72f73c-4528-19e6-b781-806e6f6e6963} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\Microsoft\Boot\memtest.efi 
description             UEFI: Windows memtest.efi 
 
Firmware Application (101fffff) 
------------------------------- 
identifier              {4c72f73d-4528-19e6-b781-806e6f6e6963} 
device                  partition=E: 
path                    \EFI\BOOT\BOOTX64.EFI 
description             UEFI:  Mass Storage Device 
 
Firmware Application (101fffff) 
------------------------------- 
identifier              {b650944c-0267-11e6-92b6-806e6f6e6963} 
description             Hard Drive  
 
Windows Boot Loader 
------------------- 
identifier              {default} 
device                  partition=C: 
path                    \Windows\system32\winload.efi 
description             Windows 7 
locale                  pl-PL 
inherit                 {bootloadersettings} 
recoverysequence        {d0745f20-0278-11e6-b719-a8be474678e9} 
recoveryenabled         Yes 
osdevice                partition=C: 
systemroot              \Windows 
resumeobject            {b96bab4d-19f2-11e6-83bc-806e6f6e6963} 
nx                      OptIn 
 
Windows Boot Loader 
------------------- 
identifier              {d0745f20-0278-11e6-b719-a8be474678e9} 
device                  ramdisk=[C:]\Recovery\d0745f20-0278-11e6-b719-a8be474678e9\Winre.wim,{d0745f21-0278-11e6-b719-a8be474678e9} 
path                    \windows\system32\winload.efi 
description             Windows Recovery Environment 
inherit                 {bootloadersettings} 
osdevice                ramdisk=[C:]\Recovery\d0745f20-0278-11e6-b719-a8be474678e9\Winre.wim,{d0745f21-0278-11e6-b719-a8be474678e9} 
systemroot              \windows 
nx                      OptIn 
winpe                   Yes 
 
Resume from Hibernate 
--------------------- 
identifier              {b96bab4d-19f2-11e6-83bc-806e6f6e6963} 
device                  partition=C: 
path                    \Windows\system32\winresume.efi 
description             Windows 7 
locale                  pl-PL 
inherit                 {resumeloadersettings} 
filedevice              partition=C: 
filepath                \hiberfil.sys 
debugoptionenabled      No 
 
Windows Memory Tester 
--------------------- 
identifier              {memdiag} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\Microsoft\Boot\memtest.efi 
description             Diagnostyka pamieci systemu Windows 
locale                  pl-PL 
inherit                 {globalsettings} 
badmemoryaccess         Yes 
 
EMS Settings 
------------ 
identifier              {emssettings} 
bootems                 Yes 
 
Debugger Settings 
----------------- 
identifier              {dbgsettings} 
debugtype               Serial 
debugport               1 
baudrate                115200 
 
RAM Defects 
----------- 
identifier              {badmemory} 
 
Global Settings 
--------------- 
identifier              {globalsettings} 
inherit                 {dbgsettings} 
                        {emssettings} 
                        {badmemory} 
 
Boot Loader Settings 
-------------------- 
identifier              {bootloadersettings} 
inherit                 {globalsettings} 
                        {hypervisorsettings} 
 
Hypervisor Settings 
------------------- 
identifier              {hypervisorsettings} 
hypervisordebugtype     Serial 
hypervisordebugport     1 
hypervisorbaudrate      115200 
 
Resume Loader Settings 
---------------------- 
identifier              {resumeloadersettings} 
inherit                 {globalsettings} 
 
Device options 
-------------- 
identifier              {d0745f21-0278-11e6-b719-a8be474678e9} 
description             Ramdisk Options 
ramdisksdidevice        partition=C: 
ramdisksdipath          \Recovery\d0745f20-0278-11e6-b719-a8be474678e9\boot.sdi


Are they correct?

As for rebuilding bcd, please find that in my 1st post, I mentioned already in the 1st post that I already did try "bootsect /rebuildbcd".

and one last thing....something odd just happened ...the Xubuntu BIOS boot entry is back ! (after the booting to Windows 7 iso Reapir Console + bcdedit + reboot).

I can't believe... what the hell is going on...opps it seems that Xubuntu still is alive...wow
> 
[quote]
Windows Boot Manager 
-------------------- 
identifier              {17a8052c-1f41-11e6-bd45-902b346f5367} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\ubuntu\wubildr\shimx64.efi 
description             Xubuntu 
locale                  pl-PL 
inherit                 {globalsettings} 
default                 {default} 
displayorder            {default} 
toolsdisplayorder       {memdiag} 
timeout                 30 

[/quote]

What the...
something overwrites Windows boot with Xubuntu boot

---

### Post by hakuna_matata on 2016-07-08
> **marcinoo said:**
> 
What the...
something overwrites Windows boot with Xubuntu boot
Windows writes all "Windows Boot Manager" entries to EFI firmware. Xubuntu entry still exists because uninstaller deleted nothing but I am wondering why you cannot select the entry for "Windows Boot Manager" entry for Windows in the EFI menu, too.

BCD says it is in the EFI menu
> ```
displayorder            {bootmgr}
```

and the "Windows Boot Manager" entry for Windows is here:
> ```
Windows Boot Manager 
-------------------- 
identifier              {bootmgr} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\Microsoft\Boot\bootmgfw.efi 
description             Windows Boot Manager 
locale                  pl-PL 
inherit                 {globalsettings} 
default                 {default} 
displayorder            {default} 
toolsdisplayorder       {memdiag} 
timeout                 30 
```

Maybe a Windows 7 issue because UEFI mode is not standard mode.

Nevertheless, if uninstaller works, in your case it deletes this entry:

> ```
Windows Boot Manager 
-------------------- 
identifier              {17a8052c-1f41-11e6-bd45-902b346f5367} 
device                  partition=\Device\HarddiskVolume1 
path                    \EFI\ubuntu\wubildr\shimx64.efi 
description             Xubuntu 
locale                  pl-PL 
inherit                 {globalsettings} 
default                 {default} 
displayorder            {default} 
toolsdisplayorder       {memdiag} 
timeout                 30 
 
```

with
```
bcdedit /delete {17a8052c-1f41-11e6-bd45-902b346f5367} /f
```

{17a8052c-1f41-11e6-bd45-902b346f5367} is the GUID from your log, too:
> ```
05-21 12:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {17a8052c-1f41-11e6-bd45-902b346f5367}

```


edit:

> **marcinoo said:**
> 
Are they correct?

IMHO, yes.

---

### Post by marcinoo on 2016-07-08
Yep, I have no "Windows Boot Manager" entry in BIOS nor in BIOS boot menu, that is odd.

And even if I as already mentioned created a similiar entry called  "UEFI: Windows bootmgfw.efi", despite the fact that it does appears in the bios boot menu, it still does not boots (as I already mentioned: after a timeout (10s) with a Gigabyte logo appearing on screen, it boots **a next device**). That is also odd.

---

### Post by oldfred on 2016-07-08
Moved to Windows sub-forum since really Windows issues.

I do not know Windows 7 nor BCD well, so cannot help.

But UEFI Windows does boot from ESP - efi system partition and that must have boot flag. You mentioned earlier that you moved it to the main Windows partition. Make sure you have only one partition with boot flag (active in Windows) and it is ESP.
And the BCD that is used to boot is the one in the ESP, not the one you added to main install partition when you tried to repair in BIOS mode.

---

### Post by marcinoo on 2016-07-08
It already has boot flag, and it is the only partition with boot flag:

> [https://i.imgsafe.org/fb18d00f21.png](https://i.imgsafe.org/fb18d00f21.png)


> **oldfred said:**
> You mentioned earlier that you moved it to the main Windows partition. Make sure you have only one partition with boot flag (active in Windows) and it is ESP.

I did not change any flags. Where did I mention about that?

I only know that it is WUBI that broke my Windows 7.

1) On a working dual boot Windows 7 & Xubuntu, I booted into Windows 7, and went into Add/Remove Programs and clicked on Uninstall Xubuntu(WUBI)
2) It did not want to Uninstall
3) So I removed Xubuntu folder manually.
4) I rebooted PC and...Windows 7 does not boot anymore.

---

### Post by oldfred on 2016-07-08
First post where you were doing BIOS type repairs. Which would have been correct if BIOS, not UEFI.

> select partition (I choosed Windows 7 partition)
detail partition (it was unactive, so)

---

### Post by marcinoo on 2016-07-08
OK I did try but do you realise that the flag has not been set:

> but I received a feedback:

 	 		 			 			 				The selected disk is not a fixed MBR disk. Only on fixed MBR disks it's possible to mark a disk as active. 			 		 

?

Because the MBR commands I had try, don't work on GPT disks.

---

### Post by marcinoo on 2016-07-09
Ok, that was an extremely odd issue. My Win7 got broken and ubootable for 4 days for an unknown reason and now it works back for an unknown reason. Because it was impossible in any way to solve this problem by no one, I decided to restore a full, 2-months-old backup of the Win7 Partition (that also includes EFI partition as well) by EaseUS Todo Backup Free 9.2 bootable iso. Before I started the restoration, I also made a backup of the current Win7 Partition. After the successfull restoration of the old Win7 backup, I rebooted my PC and...Win7 still was unbootable. I checked the BCD entries and they were the same. So I restored the backup of the current Win7 partition, rebooted the PC and... Win7 boots ! but....no desktop yet...it throws on a black screen:

> [https://i.ytimg.com/vi/etm0dzZ1DE0/maxresdefault.jpg](https://i.ytimg.com/vi/etm0dzZ1DE0/maxresdefault.jpg)

> 
Windows Error Recovery

Windows failed to start. A recent hardware or software change might be the cause.

If windows files have been damaged or configured incorrectly, startup repair can help diagnose and fix the problem. If power was interrupted during startup, chose start windows normall7



Launch Startup repair (recommended)

Start Windows Normally


I selected "Start Windows Normally" but it returned to the same screen.

So I selected "Launch Startup repair (recommended)",
the computer rebooted and booted into Startup Repair,
it started repairing which lasted a few minutes,
then it throwed:

> [http://www.sevenforums.com/attachments/tutorials/133609d1295703179-startup-repair-infinite-loop-recovery-image07_cannotfix.jpg](http://www.sevenforums.com/attachments/tutorials/133609d1295703179-startup-repair-infinite-loop-recovery-image07_cannotfix.jpg)
> [https://2.bp.blogspot.com/-X18l9Owkqyg/Vzrj9zbUFqI/AAAAAAAAAOA/tcRL3prC6x8WzppzhjHP1hVuBna-IKydQCLcB/s1600/Hows3.jpg](https://2.bp.blogspot.com/-X18l9Owkqyg/Vzrj9zbUFqI/AAAAAAAAAOA/tcRL3prC6x8WzppzhjHP1hVuBna-IKydQCLcB/s1600/Hows3.jpg)

> Startup Repair

Windows cannot repair this computer automatically

"If you have recently attached a device to this computer, such as a camera or portable music player, remove it and restart your computer. If you continue to see this message, contact your system administrator or computer manufacturer for assistance.

Click Finish to exit and shut down the computer


> 
Startup Repair

Startup Repair cannot repair this computer automatically

Sending more information can help Microsoft create solutions.

Send information about this problem (recommended)

Don't send

Show problem details:

Problem signature:

Problem Event Name: StartupRepairOffline
Problem signature 01 ...
Problem signature 02 ...
Problem signature 03 ...
etc...


Then I selected "Send information about this problem (recommended)"

And then "View diagnosics and repairs details"

And it showed me:

> 
Startup Repair
Diagnosis and repair details:
Root cause found:
----------------------------
Unspecified changes to system configuration might have caused the problem.

Repair action: System files integrity check and repair
Result: Failed. Error code = 0x490
Time taken = 201959 ms

------------------------------
-----------------------------
Session details
--------------------------------


Then I rebooted the computer and...Win7 boots to desktop and works back.

I don't have a clue what the hell was going on. Was it a hardware / firmware (BIOS, HDD) or a software (Windows, WUBI, Linux) failure or a mix of both. God knows only. But a fact is that everything started after WUBI removal. These are the most annoying and inconceivable problems with computers.... which randomly appear and then disappear for no real cause. I only hope that it will not break again in a moment.

> [https://images.creators.co/image/upload/c_scale,h_524,w_700/t_mp_quality/do-you-believe-the-rumors-about-a-new-x-files-season-319785.jpg](https://images.creators.co/image/upload/c_scale,h_524,w_700/t_mp_quality/do-you-believe-the-rumors-about-a-new-x-files-season-319785.jpg)

---

### Post by hakuna_matata on 2016-07-09
> **marcinoo said:**
> 
Because the MBR commands I had try, don't work on GPT disks.
Some MBR commands worked because the bootinfoscript found a boot loader in the MBR of your disks:

> ```
 => Windows 7/8/2012 is installed in the MBR of /dev/sda.

```

A boot loader in the MBR is not needed for UEFI mode. My bootinfoscript reports for a GPT disk: 
```
  => No boot loader is installed in the MBR of /dev/sda.
```

It is possible to use GPT disks in legacy BIOS mode but it could be the reason for problems. e.g. Maybe your EFI firmware tries to boot with MBR boot loader in legacy BIOS mode if EFI mode fails. 

> **marcinoo said:**
> 
2) It did not want to Uninstall

The Wubi uninstaller didn't uninstall Xubuntu but it didn't change anything. So it could not break Xubuntu or Windows.
> **marcinoo said:**
> 
3) So I removed Xubuntu folder manually.
  
Since then it has been not possible to boot into Xubuntu or to boot into GRUB2 menu within Xubuntu.
So you broke Xubuntu of course but IMHO you didn't break Windows. 

Wubi don't remove the EFI menu entry for Windows during installation. It creates an additional entry. 
So it should always possible to run Windows from EFI menu. Has there never been an EFI menu entry for Windows since you installed Xubuntu with Wubi ?

Did you change the EFI menu entry for Windows since you installed Xubuntu with Wubi ? 
Maybe, you wanted to change the boot order.

As I wrote if uninstaller works it removes the additional entry which was created during installation. But if you uninstall it manually, it is also possible to use the additional entry for Windows by changing the path of the boot loader.
```
bcdedit /set {17a8052c-1f41-11e6-bd45-902b346f5367} path \EFI\Microsoft\Boot\bootmgfw.efi
```
To clarify it is not still Xubuntu, you can also change the description of the entry:
```
bcdedit /set {17a8052c-1f41-11e6-bd45-902b346f5367} description "Windows"
```

edit: As I wrote my answer I didn't read your last post.

---

### Post by marcinoo on 2016-07-09
> **hakuna_matata said:**
> Has there never been an EFI menu entry for Windows since you installed Xubuntu with Wubi ?

I don't remeber exactly, but as far as I remember, there has never been EFI menu entry for Windows visible, no "Windows Boot Manager" nor anything in BIOS nor in BIOS boot menu, even before I installed Xubuntu, even if the entry (Windows Boot Manager) does psychically exist as seen in bcdedit, maybe it is hidden or disabled, I don't have a clue. An entry I always used to boot Windows 7 BIOS MBR was "PO Samsung 850 EVO 120GB". After I switched from Windows 7 BIOS MBR to Windows 7 UEFI GPT, it was "UEFI Samsung 850 EVO 120GB". After I encrypted my SDD with sedutil I had to select "UEFI Samsung 850 EVO 120GB" two times. The first time I select "UEFI Samsung 850 EVO 120GB", instead of booting Windows 7 it asks me for the password, I enter the password, and the computer reboots, after the computer reboots I select "UEFI Samsung 850 EVO 120GB" the second time and now Windows 7 boots normally. After I installed Xubuntu-WUBI the entry "UEFI Samsung 850 EVO 120GB" ceases to appear the second time (after the reboot), but I then select Xubuntu >> Windows Boot Loader and Windows 7 boots normally just like missing "UEFI Samsung 850 EVO 120GB". I thought it was WUBI who removed "UEFI Samsung 850 EVO 120GB" and moved it and renamed to Xubuntu >> Windows Boot Manager. After I removed Xubuntu folder, the Xubuntu boot entry completeely failed to load, and at the same time "UEFI Samsung 850 EVO 120GB" still was missing (the second time - after entering the SSD password and after rebooting). Thus I was completely unable to boot Windows 7, no Win7 entry. Adding custom Windows boot entries did not work too, as seen and I don't know why. As for the "UEFI Samsung 850 EVO 120GB", maybe it is the "Windows Boot Manager", maybe during boot, BIOS (motherboard) rename / redirect "Windows Boot Manager" to "UEFI Samsung 850 EVO 120GB" and thus the both entries are a single one just with different names, but as seen now under Windows 7 in 
> EasyUEFI Free[http://www.easyuefi.com/](http://www.easyuefi.com/)
 they have diferrent EFI files:

> 
Description:Windows Boot Manager
GPT partition GUID:{1C0C4722-5359-49CD-A689-4392436E77D6}
Partition number:1
Partition starting sector:2048
Partition ending sector:206847
File path:\EFI\Microsoft\Boot\bootmgfw.efi

Description:UEFI: Samsung SSD 850 EVO 120GB
GPT partition GUID:{1C0C4722-5359-49CD-A689-4392436E77D6}
Partition number:1
Partition starting sector:2048
Partition ending sector:206847
File path:\EFI\BOOT\BOOTX64.EFI


And GPT partition GUID changed too.

My Win7 boots now, because "UEFI: Samsung SSD 850 EVO 120GB" is back and appears now in boot menu the second time (after enterting the password and rebooting the computer). And there is no Windows Boot Manager visible in BIOS nor in BIOS Boot Menu.

My motherboard is:

> Gigabyte GA-B75-D3V [http://www.gigabyte.com/products/product-page.aspx?pid=4149#ov](http://www.gigabyte.com/products/product-page.aspx?pid=4149#ov) BIOS is the newest one - F9

> **hakuna_matata said:**
> 
Did you change the EFI menu entry for Windows since you installed Xubuntu with Wubi ? 
Maybe, you wanted to change the boot order.

Nope, I did not touch anything.

---

### Post by hakuna_matata on 2016-07-09
Unfortunately, there are a lot of different EFI firmwares. There are comfortable EFI firmwares where you can edit your EFI boot menu. Other EFI firmwares are spartan and have some issues.  It seems that you have the second one.
                             > EasyUEFI Free[http://www.easyuefi.com/](http://www.easyuefi.com/)
IMHO it is a helpful tool but some years ago I had also an issue. I saw 2 entries for "Windows Boot Manager" and I removed one. But after reboot both entries were removed and Windows was unbootable. Probably, this issue is fixed in newer version of EasyUEFI but maybe it is not only an issue of EasyUEFI. It could be an issue of Windows or/and a buggy  firmware, too.
> the Xubuntu boot entry completeely failed to load
The GRUB2 loader was loaded but the GRUB2 menu was not found. But nevertheless, it would be possible to boot manually into Windows with GRUB2 commands. e.g. if your EFI partition is on first disk and first partition ('hd0,gpt1') 
```

insmod part_gpt
insmod fat
set root='hd0,gpt1'
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
```

---

### Post by oldfred on 2016-07-09
It looks like because you encrypted system, it does not use standard UEFI boot entry.

Have seen many Windows encrypted systems with BIOS and there was no way to restore a standard Windows boot loader, either the 'works like Windows boot loaders' Linux can add, or even the "official" Windows boot loader. Sometimes only a copy of MBR would work, if user had that. And some  encrypted systems had there own MBR repair or recovery tools.

---

### Post by hakuna_matata on 2016-07-09
> **oldfred said:**
> It looks like because you encrypted system, it does not use standard UEFI boot entry.
Thank you, oldfred. IMHO, you have found the reason.   

[Here]("https://github.com/Drive-Trust-Alliance/sedutil/issues/27") is an issue for sedutil that confirms the possibility of lost UEFI boot entries.

So we can say that the unbootable Windows 7 was not the blame of Wubi.

---

