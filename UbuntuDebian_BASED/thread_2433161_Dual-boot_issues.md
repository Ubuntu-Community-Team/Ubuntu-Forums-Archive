---
title: "Dual-boot issues"
date: 2019-12-14
forum: Ubuntu/Debian BASED
---

### Post by hugomilan on 2019-12-14
Hi,

I have installed an Ubuntu 19.10 flavor (Pop!_OS) and I lost access to my Windows 10. I have run boot-repair (log here: [https://paste.ubuntu.com/p/yY8gCYXjCH/](https://paste.ubuntu.com/p/yY8gCYXjCH/) ), ntfsfix, remove_hiberfile, etc., without success. My current partition scheme is the following:
/dev/nvme0n1p1   /boot/efi                                    vfat       
/dev/nvme0n1p2   / for Pop!_OS 19.04                          ext4       
/dev/nvme0n1p3   /home shared between Pop!_OS 19.04 and 19.10 ext4       
/dev/nvme0n1p4   / for Pop!_OS 19.10                          ext4       
/dev/nvme0n1p5   swap                                         swap       
/dev/sda1        my back-up files                             ext4
/dev/sda2        Windows partition                            ntfs       
/dev/sda3        Windows recover partition (I believe)        ntfs

Any help getting back access to Windows 10 will be greatly appreciated.
Thanks,
Hugo

---

### Post by howefield on 2019-12-14
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2019-12-14
You have UEFI system and it looks like all installs are UEFI.
Grub only boots working Windows. So normally you then just boot Windows from UEFI boot menu.
And often issue is just Windows turned fast start up back on.

Repair does not show all the details on NVMe drives. 
In ESP in nvme0n1p1/efi is there a /EFI/Microsoft folder?

You show Windows fast start/hibernation is on. That has to be off to dual boot.
After you boot into Windows from UEFI, be sure to turn that off.

        Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
You will need to use your Windows repair/recovery flash drive or installer's repair mode and fix Windows. The UEFI boot entries look like either drive was disconnected or boot partition is missing.
But GUID shown is the same for all but the Ubuntu UEFI entry and is GUID/partuuid of your ESP on the NVMe drive. 


You have a lot of duplicate UEFI boot entries. You need to remove those.
BootOrder: 000C,000A,0003,0004,0017,0005,0002,0007,0001,0008,0006,0009,000B,0000

I would remove all but: 3,4, and 000A. 
The others look incorrect. And only 000A is a typical UEFI boot entry. But I would leave the IP entries also.

        # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 
    
Then use Windows repair disk to add correct Windows entry. Boot into Windows and turn off fast start up, and make any other repairs, so grub can boot it. 
I normally have seen Windows ESP on same drive as install. But understand that if another drive is default boot in UEFI/BIOS, it may put boot files there. So hopefully repair will see install in sda, but install new .efi boot files into ESP on NVMe drive.

Be sure to always boot in UEFI boot mode. Boot-Repair mentions adding a bios_grub partition but that is only for BIOS boot which you do not want. Only boot in UEFI mode for install and repairs.

---

### Post by yancek on 2019-12-14
Was windows 10 pre-installed on this computer?  Boot repair shows the windows disk as GPT so it should have been an EFI install with an EFI partition on that drive but there is none?
Boot repair shows an EFI partition on the SSD:  /dev/nvme0n1p1   A67E-1B44   No windows EFI boot files show but there is an entry for an EFI windows boot in the efibootmgr output; Boot0002.  How many times did you install or try to install PopOS?  You have 9 EFI entries for it, you only need 1.  You also have 1 EFI entry for ubuntu.  You could try to go into the BIOS on boot to the boot options and select Boot0002 which is probably named Windows or OS boot manager.  Don't think it will work as you don't seem to have any EFI boot files for windows.  At least they don't show in the boot repair output.

The /etc/default/grub file is there but there is no grub.cfg file showing.  That is the boot menu you see on screen.   Lines 13-139 indicate that windows is in an unsafe state and was not mounted and so no entry for windows could be created.  THis is  generally a result of having fastboot on or hibernation on in the power settings.  This cannot be changed from Linux/Ubuntu.

It's a mess, the only thing I could suggest would be to  try to access windows from the BIOS boot options.  If that doesn't work, you will need a windows installation or repair disk to repair the boot files.

---

