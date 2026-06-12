---
title: "Dual boot - win7/ubuntu windows update failed - how to restore and keep grub setup?"
date: 2019-12-14
forum: Windows
---

### Post by JimLS on 2019-12-14
Windows 7 update crashed and now won't boot.  I tried using the windows install CD and it gives me an error that it isn't compatible even though its the install media I used originally.  It's been some time since I set this all up so I don't remember all the details.  Want to restore this with a minimum of effort.  Probably should migrate to win10 at some point - I got the free upgrade ISO.  But first I want to restore.  I have a windows 7 repair disk.  Thinking the windows restore will overwrite grub so grub will need to be re-setup.  Should I back up any particular files for grub?  I copied the obvious files from windows and ubuntu to a USB harddrive backup.

Here is my boot info script file.  sdc is a USB backup drive and not normally part of the system.  sdb is a data drive.  The os's are on sda.

[https://pastebin.com/embed_js/i99t65dL](https://pastebin.com/embed_js/i99t65dL)

---

### Post by oldfred on 2019-12-14
Moved to Windows sub-forum since Windows 7 issue.
Note that Windows 7 reaches EoL - End of Life  Jan 2020.

Have you tried chkdsk on all your NTFS partitions?

---

### Post by JimLS on 2019-12-14
To run chkdisk I would need to be able to boot windows so that isn't a possibility until I fix booting.  Grub seems to work and I can boot ubuntu.

---

### Post by oldfred on 2019-12-14
Years ago I ran chkdsk from my Windows 7 repair flash drive on my XP install. It fixed more than what XP's chkdsk did, but changed PBR - partition boot sector from XP type to 7 type. And then I had to fix that.

You should also be able to use a Windows 7 installer but go into repair mode. 
Or download Windows 10 installer with repair/recovery.

---

### Post by JimLS on 2019-12-14
Tried to run the windows 7 repair disk.  It sees the windows installation but Boot repair doesn't find a problem.  Restore shows the update on Dec 10th that crashed but when trying to restore it crashes.

---

### Post by JimLS on 2019-12-14
Trying to restore using several different restore points gives the same error:

The instruction at 0xfb5d584d referenced memory at 0x00000008.  The memory could not be read.  Click on ok to terminate the program

I did get one restore of a removal of program to start but in finishing up it said it failed.  Command prompt seems to be the only thing that works but I am unsure what to do there.

---

### Post by oldfred on 2019-12-14
Boot-Repair is primarily for Linux booting issue, not file corruption on any Windows or Linux system.
With Windows in BIOS mode it can install a Windows type boot loader to MBR, so you can directly boot Windows. But often better to install Windows boot loader with fixMBR from Windows repair.

Grub only boots working Windows. 
If any issue at all, try installing Windows boot loader to MBR and then see if it works.

---

### Post by JimLS on 2019-12-14
Boot repair I mentioned is a part of the Windows 7 repair disk - nothing to do with Linux.  

Windows boot loader is now in the windows partition.  How do I install in MBR and how do I back up my grub config so I can restore it easily.  It's been a while since I messed with it.

---

### Post by oldfred on 2019-12-14
It really is easy to reinstall grub, so we do not normally back it up. Not only is it in MBR, but in sectors after MBR.

You can use Boot-Repair to reinstall grub, using its advanced options. Use Ubuntu live installer in live mode & add Boot-Repair.
        [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If just reinstalling grub from live installer:

       
 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 in example if not your Linux partition:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub 

If separate /boot you have to also mount that. And if UEFI install with ESP, you need to mount that & probably better to use Boot-Repair or full chroot.

      
  chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by JimLS on 2019-12-16
I installed Win10 to another partition and have 10 and 7 booting although 7 has some issues with programs that have lost their settings.  I am going to move to 10 for windows alongside Ubuntu so am not going to mess with 7 except to get some config files and such.  Now I need to resolve some boot loader issues.  By default it boots to selection of 7 or 10 with windows bootloader.  Through some experimentation I found that sdb, a conventional hard drive used for storage only, has the windows loader - at least thats the default boot device.  If I select sda I get the grub boot loader menu.  Haven't checked that the windows entries work yet.  Would like to just have one menu of Ubuntu, 7 or 10.  System is uefi I think.  Some boot options show as AHCI.

---

### Post by oldfred on 2019-12-16
Windows normally puts all its boot files into one boot partition if BIOS or ESP if UEFI.
And then BCD is the menu on what Windows to boot.

There are work arounds for creating duplicate boot if BIOS or duplicate /EFI/Windows partitions. You only can boot one from UEFI/BIOS, but grub can find both if configured correctly & once boot has started, it should not matter. Issue on Windows 10 fast start up is there whether UEFI or BIOS, it must be off. I think it has to be off to dual boot Windows 7.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by JimLS on 2019-12-18
I discovered in bios that the boot order had "windows boot manager" first and reset that to the drive name.  When I tried to boot it gave an error of file /boot/grub/i386-pc/normal.mod not found.  So grub is now trying to boot and not sure what the problem is with the missing file.  

I looked at the power settings in win10 and fast boot is turned off.  Not sure why I got the message that it had a similar issue.

---

### Post by oldfred on 2019-12-18
That typically is that you have grub installed twice, one old one & it is booting the older one which is not totally configured anymore.

Windows does turn fast boot back on. Or hibernation could be set. Or NTFS could need chkdsk.  My old XP took 5 min to boot. After chkdsk it only took 3 min, but it had no other indication that system needed chkdsk.  (Ubuntu booted in 40 sec on that old system).

Need to see Summary Report from Boot-Repair.

---

### Post by JimLS on 2019-12-19
Is it possible I have some mix of UEFI and legacy?  Gparted reports the disk as "msdos" partitioning but windows 10 system info states it is UEFI mode.  My bois is american megatrends from 2013 and seems to allow either (on some CDs if I look at boot options it offers to boot the disk in UEFI or AHCI but I think if I boot automatically it goes to UEFI.  I would expect win10 would have refused to install to the drive if it was MBR but the install cd was running in UEFI mode...

I ran gparted for this from a Xubuntu 18.04 live cd.  The same cd wouldn't run boot-repair (installed via command line) in UEFI mode and said I needed to boot in legacy mode.  So I booted and selected AHCI option.  But I am a little scared now to run boot-repair as things seem very weird...

I was wanting to keep the old system around for a while while getting the new system going but perhaps the best bet is to wipe the drive and start over?

Just ran fdisk -l /dev/sda
which reported Disklabel type:  dos
which I think means the disk is MBR and seems to agree with boot-repair message.

Is MBR/GPT independent of AHCI/UEFI?  I am not clear on the terminology.

---

### Post by oldfred on 2019-12-19
Windows only boots in UEFI mode from gpt partitioned drives.
Windows only boots in BIOS mode from MBR(msdos) partitioned drives.

How you boot install media UEFI or BIOS, is then how it installs. You can normally boot flash drive or DVD/CD in either mode, but may require UEFI/BIOS settings to allow boot. But default boot of installed system depends on settings in UEFI/BIOS and may not match how you have installed.

With new UEFI systems and if Windows is installed in UEFI mode, you should always boot in UEFI mode. If you do not seem to be able to boot flash drive/DVD installer it could be UEFI settings, what choice you made, ISO not quite correct, or issue with DVD or flash drive. I used to have a lot of issues with bad burns, so changed to use flash drives only. 

Boot-Repair report shows all the details.

---

### Post by JimLS on 2019-12-19
> **oldfred said:**
> Windows only boots in UEFI mode from gpt partitioned drives.
Windows only boots in BIOS mode from MBR(msdos) partitioned drives.



That doesn't appear to be the case.  When booted into the SSD win10, disk part reports the disk as non-GPT (no asterisk in the GPT column) which would be MBR but system information reports "Bios mode  UEFI".  

I think what may have happened is the install media booted in UEFI (default mode) and installed UEFI.  I found one place that said this was possible and another that said it wasn't.  

But I could be all wrong too...

Looks like I need to reinstall win10 by booting the install cd in AHCI mode?

---

### Post by JimLS on 2019-12-19
Here is the boot repair summary

[http://paste.ubuntu.com/p/bmB35hDDmK/](http://paste.ubuntu.com/p/bmB35hDDmK/)

---

### Post by yancek on 2019-12-19
Lines 577-589 give information on windows EFI files but  there is nothing there that is Ubuntu.  The drive shows as Legacy (msdos) on line 52.  Windows won't install UEFI on that drive.  Do you have Legacy/CSM enabled in the BIOS?  Boot repair also shows UUID=6AACE2B7ACE27CC7    /boot/efi    ntfs    defaults    0    1 in /etc/fstab of Ubuntu. That is on line 464.  An EFI partition should be on a vfat filesystem not ntfs and that UUID is sda3, not sure what that is on your system but it does have windows boot files.  sda1 is marked as active/bootable.   Enable Legacy/CSM boot in the BIOS firmware.

Boot repair shows you have Grub in the MBR of the drive pointing to the Grub files on sda2.  Are you able to boot Ubuntu?  If so, do that and run:  sudo update-grub

---

### Post by JimLS on 2019-12-19
Thanks but I have been messing with this for several days so just started fresh.  I have backups so set the disk to GPT and reinstalled everything.

---

### Post by oldfred on 2019-12-19
Report shows MBR and BIOS boot install of Windows.
You can use Boot-Repair's advanced modebooted in BIOS mode,  to totally reinstall grub to convert from UEFI to BIOS boot. Ubuntu will let you install in UEFI mode to a MBR drive, but that cannot work if Windows is on same drive in BIOS mode. Windows in BIOS mode has to have boot flag on the primary NTFS partition with Windows boot files. UEFI has to have an ESP, and that is set with boot flag. Only one boot flag per drive, so you cannot have Windows boot flag & ESP boot flag.

Or you can convert drive to gpt and then totally reinstall both Windows & Ubuntu.

---

