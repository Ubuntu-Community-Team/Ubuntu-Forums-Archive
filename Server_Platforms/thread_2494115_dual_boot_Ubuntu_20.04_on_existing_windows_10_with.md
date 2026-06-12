---
title: "dual boot Ubuntu 20.04 on existing windows 10 with existing Raid 1"
date: 2024-01-05
forum: Server Platforms
---

### Post by tross9 on 2024-01-05
I'm trying to install Ubuntu Server 20.04 (may upgrade later) on an existing windows 10 computer ( raid 1  mirror via Intel rapid storage (bios)  ).

   I'm stuck at the "storage conf" screen.  "Done" is grayed out.

pre install steps:
   booted to windows 
    shrank the 931 Meg partition into two 467 and 463 partitions
           formatted the 463 to exfat

   rebooted and started the Ubuntu install

"storage conf" screen:

   available device:
    partition 1  existing already formatted NFTS  not mounted 100 M
    partition 2  existing already formatted NFTS  not mounted 467 G
    partition 3  existing extended unused                               463 G  
    partition 4  existing already formatted NFTS  not mounted 511 M
     
        partition 5  existing logical already formatted as exfat, not mounted   463 G

I selected Partition 5 
    selected edit 
       changed the format to EXT4
         changed the mount point to /
  and saved changes.

but the "Done" option is grayed out.

I was following a Video on dual boot ( windows and Ubuntu) and the next step was to allocate /boot in an existing FAT partition which I do not have.

what am I missing?
    do I need to go back to windows and create another exfat partition for the /Boot?

TIA

Tim.

---

### Post by oldfred on 2024-01-05
If you have an extended partition that is the very old MBR (msdos) partitioning from the 1980's.
Windows boot in old BIOS mode requires MBR.
But since release of Windows 8 in 2012, Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives.
Is system an old upgrade of Windows  7 which usually was BIOS/MBR, but could be UEFI/gpt?
Or did you boot Windows installer in old BIOS mode, so it installed in old BIOS mode to MBR drive?

Best if all systems are installed in same boot mode, or all UEFI or all BIOS. And required to be in same boot mode if on same drive.
UEFI systems offer two ways to boot installer for both Windows & Linux, one clearly UEFI and one BIOS. New UEFI systems since about 2020 are UEFI only, but my Dell with 11th Gen Intel is UEFI only but Dell still calls it BIOS.

If you convert Windows to UEFI mode, it has to convert to gpt which erases entire hard drive, so good backups required.
You only need the ESP - efi system partition for UEFI boot, as FAT32 with esp,boot flags. Windows requires boot flag on its BIOS boot partition and only one boot flag per drive, so that is why systems must be in same boot mode.

If system is UEFI hardware, better to use UEFI/gpt, but conversion of Windows is a hassle unless just installed, so nothing to lose.

---

### Post by tross9 on 2024-01-06
Oldfred, Thanks for the quick reply.

  yes, it was a windows 7 upgrade to windows 10.

this machine is a testing system, so backing up the system is not need and I can just start from scratch, if needed.
  

(I don't have a windows 10 key, so upgrade is only option.)

I think I have three options:     ( would to prefer having the system as a workstation or server as I need it)

 1) see if I have a windows 8 disc and key , then install it, then Ubuntu.
2) install Ubuntu then install windows 7 and upgrade to 10.
3) just install Ubuntu only

do you think option 2 would work?

Again Thanks

Tim

---

### Post by oldfred on 2024-01-06
Is system UEFI or BIOS?
Issue with Windows 7 is that most installs were BIOS/MBR. But later Windows 7 ISO or a manual update to ISO would allow UEFI install with Secure Boot off. Windows 7 does not support UEFI Secure boot but can be an UEFI install.
How you boot install media, UEFI or BIOS for both Windows & Ubuntu is then how it installs.

I do not know nor use RAID. But my understanding it is for uptime on servers, not backup.
Some desktop installs with BIOS RAID, just break RAID and then have two drives. But then all data may be lost.

---

### Post by tross9 on 2024-01-07
Oldfred,

 according to window system info the bios entry is  "legacy" -- so I would say the installed windows version is Bios.

as to the raid, correct , it is not for backup but for uptime and protecting the data on the drive , if one drive fails , it can be replaced before the other fails.

Tim

---

