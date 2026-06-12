---
title: "Ubuntu/Windows 10 crash and reboot loop [SOLVED]"
date: 2022-03-29
forum: Windows
---

### Post by gangliaghost on 2022-03-29
SOLVED: Initial bootloader issue caused by me being dumb and thinking  Windows would install where I told it to while other drives were  connected. Got Windows bootloader off the M2 by using secure erase +  feature in updated bios settings, all other attempts failed. Attempted reinstall of Windows and the  SSD melted due to faulty/misguided SATA cable specifications. Will try  again with a new SSD eventually, but thread will be closed and a new one  will open with any other issues I run into.

ORIGINAL THREAD POST:

Hello, it has been a week or two and I cannot find a solution to my issues. 

I originally had just Ubuntu in my 1 tb M.2, but I decided to purchase another SSD and put Windows 10 on that. The idea was to create isolated drives on which both OS would reside. At first, the install seemed to go alright, and Windows ran and I was able to set up boot options in the BIOS and choose which OS to boot on start up. Ubuntu was default option. Both ran when chosen during boot. I was in Windows 10 when the OS suddenly crashed. I received an error screen and Windows attempted self repair, and then the computer went into a reboot loop, where if Windows attempted to boot, I would receive a boot screen and then the system would suddenly restart. I attempted to repair from my original boot media, to no avail. Since I had no files on the drive, I did another clean install of Windows and attempted again. Before attempting the clean install, I found that my drive had been completely locked into read-only and I could not even access C: to find any crash logs. I made sure to delete all partitions and repartition the drive so I would have the OS on one partition and any software and files associated on Windows in the other partition. I did the install. Half way through a download of a steam game, windows gave a fatal error and shut down. On the recovery screen during boot, I was given "a required device isn't connected or can't be accessed" and  "Error Code: 0xc000000e". I also found a prompt that pointed to a srttrail.txt error. This time in the command prompt, I was able to remove read-only setting and find some logs, including the srttrail.txt. It contained some info such as a disk failure diagnosis that was successfully completed, but didn't seem to contain any explicit reason for the crash. All other crash logs had unknown errors. My SSD is currently unplugged from the power source, as I've been also having ongoing issues with USB hubs in Ubuntu and I was seeing if it was a power issue. Ubuntu has been running fine this whole time. While checking BIOS settings, I noticed that the Windows 10 bootloader is installed on the same drive as my ubuntu bootloader, the M.2, despite me trying to keep the two separate. The main Windows OS partition is in the SSD, while the bootloader for Windows is in the M.2.

My next planned step is to disconnect all drives other than the SSD Windows 10 should go on, reinstall Windows 10 on the SSD and hopefully keep the Windows bootloader on the SSD. Then I was going to see if I could disable automounting in Windows somehow and reconnect the other drives. However, I am worried the windows 10 bootloader on my ubuntu efi will be problematic, so is there any way to delete it? I tried rm in the terminal and and the boot is removed, but then comes back at start up. I tried directly deleting the file in the path I found, and Ubuntu says that "no such file exists" each time. I've also heard the Windows bootloader can interfere with Ubuntu so I'm worried about that. Should I cut my losses and wipe and reinstall ubuntu as well? I'm also going to try to switch out the SSD SATA power cable and see if that caused the initial crash in any way.



Hardware: 
Motherboard: MSI B450 Tomahawk
RAM: 32 GB
CPU: AMD Ryzen 5 3600 6-Core Processor
GPU: NVIDIA GeForce 2060
Power Supply: Corsair rm550x
Storage: Western Digital NVMe M.2, 1 tb; HDD 2 tb; Mushkin SSD 1 tb.

Mushkin SSD 1 tb is supposed to be the Windows 10 drive, the M.2 is Ubuntu

---

### Post by yancek on 2022-03-29
Have you gone to a windows forum to look for a solution as that is where the problem is?

In situations where you have a dual/multi boot and want to keep them separate it is best to disconnect the drive(s) you are not installing to before beginning the install.  , If you want the OS on each drive separate, create an EFI partition on the drive you are installing to and disconnect other drive(s).  On EFI system, installing a new OS will create an EFI entry for it on the EFI partition which will be a separate folder, named Microsoft for windows and ubuntu for Ubuntu.  

Deleting an EFI entry from Linux/Ubuntu is explained at the link below.

[https://askubuntu.com/questions/1112243/cannot-permanently-remove-boot-entry-using-efibootmgr](https://askubuntu.com/questions/1112243/cannot-permanently-remove-boot-entry-using-efibootmgr)

---

### Post by oldfred on 2022-03-29
Moved to Windows sub-forum since Windows issues.

Have you updated UEFI firmware & SSD firmware. That often solves issues.
But it may just be a bad SSD?

---

### Post by gangliaghost on 2022-03-29
> **yancek said:**
> Have you gone to a windows forum to look for a solution as that is where the problem is?

In situations where you have a dual/multi boot and want to keep them separate it is best to disconnect the drive(s) you are not installing to before beginning the install.  , If you want the OS on each drive separate, create an EFI partition on the drive you are installing to and disconnect other drive(s).  On EFI system, installing a new OS will create an EFI entry for it on the EFI partition which will be a separate folder, named Microsoft for windows and ubuntu for Ubuntu.  

Deleting an EFI entry from Linux/Ubuntu is explained at the link below.

[https://askubuntu.com/questions/1112243/cannot-permanently-remove-boot-entry-using-efibootmgr](https://askubuntu.com/questions/1112243/cannot-permanently-remove-boot-entry-using-efibootmgr)

Hi, I followed that thread, but when I use bootmng to remove the efi windows boot, and update grub, it appears to work. I restart my computer and the windows boot option has returned. EDIT: I tried again and am now having permissions denied.

---

### Post by oldfred on 2022-03-30
Many vendors seem to auto find the /EFI/Microsoft folder in the ESP & add the Windows boot entry. They know you are booting Windows, or at least most people are.

If you remove /EFI/Microsoft folder in the ESP if on Ubuntu drive, does it still add an UEFI entry.
Do not remove any other folders in the ESP, nor remove the ESP partition.

If totally separate drives you want an ESP with just /EFI/Boot & /EFI/Microsoft on Windows drive and only /EFI/Boot & /EFI/ubuntu on Ubuntu drive.
You can have both in one ESP and that is the default that Ubuntu uses.

Ubuntu's Ubiquity installer wants to install only to first drive.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by gangliaghost on 2022-03-30
Hi oldfred,
If I install EFI/Microsoft on the windows drive, is there any future chance it will interfere with /EFI/Ubuntu in the future if I physically reconnect the drive? I know windows sometimes changes settings during updates so is using cmd to set the m. 2 to not automount in windows 10 and using terminal to set the ssd to not automount in Ubuntu sufficient? Thanks.

Also update: Flashed bios firmware. was unable to find any way that worked to delete the windows efi and update grub because the file was always somehow restored, usually by a back up somewhere. I managed to get the command to delete the file to run through once and when I updated grub and ran efibootmgr again there were even more files in other locations. Even fresh install of Ubuntu where I told it to repartition and format the disk didn't work (windows efi sat in the exact same path) and after fiddling with nvme-cli in a grml live USB to try to sanitize the ssd, I was able to find a secure erase + feature in the BIOS. Unfortunately western digital ssd dashboard software is completely broken, so I couldn't use that. Nvme-cli was locked up and I couldn't do anything when attempting sudo format or sudo sanatize commands. Used the secure erase + in bios and luckily the ssd didn't lock up or brick or anything. Reinstalled Ubuntu, checked efibootmgr. It didn't show any boot other than Ubuntu, I update-grub and then checked again, still no windows, so at least I got the efi file off the Ubuntu drive. It's unfortunate I couldn't find a way other than nuking the drive but I didn't have anything important that wasn't backed up.

I am going to remove the m2 from the pc and attempt windows 10 install on the new ssd. I'll replace the SATA power cable and see if that helps with drive fails. Is secure erase + recommended on the new ssd? I'm wondering if that could clear up any faults that caused the crashing and also prevent complications from reinstalling windows 10 on top of itself.

Whole problem has been extremely annoying but at least I've learned a bunch in the process. I'm pretty new to this kind of stuff and I haven't been formally trained. I'd say the consequences of my ineptitude weren't too severe and I got a lesson out of it haha.

---

### Post by oldfred on 2022-03-31
Most systems do not require removal of M.2 drives as often located in difficult to get to locations.
You should have a setting in UEFI to disable or turn off the M.2 drive.

It seems most UEFI automatically create Windows UEFI boot entries, if ESP has /EFI/Microsoft folder.
And UEFI normally forgets UEFI entries. So only a Windows entry is restored when a drive is unplugged & then replugged in.
You need to use efibootmgr to update/create new ubuntu entry in UEFI if removing an Ubuntu drive, if ESP on Ubuntu drive.
If ESP on Windows drive & Windows not removed I think it normally keeps the ubuntu entry, but it of course will not work if drive unplugged. You just get grub>. But you still can boot Windows from UEFI, but not grub.

---

### Post by gangliaghost on 2022-04-03
UPDATE:
Got the windows bootloader off the M.2, haven't seen it since. I attempted removing all other drives and clean installing the SSD, but when I attempted boot, the computer wouldn't turn on and the power supply seemed dead. I was able to get a click out of it eventually, though. Did some trouble shooting and was able to get the computer to turn on by using two SATA ports on one SATA cable that I had ordered brand new from Amazon. The HDD was on one SATA port and the SSD was on another. Turned on computer, and after 5 seconds got an intense burning smell. It was specifically a resistor burning smell. I immediately shut down and disconnected everything but the SSD was the source of the burning. I can't get a return or anything, because I threw away the packaging when it initially seemed to work. Also! It wasn't even the SSD that was faulty! I did testing because at first my PSU seemed fried as well. I tested all three SATA cables I owned, and the first two checked out with a 12V and 5V reading. I got to the third cable, which was the one used when the SSD melted, and it only output 12V! I double checked the amazon page and other than saying it was compatible with a certain psu, the specifications said NOTHING about it being 12V only or incompatible with other kinds of psu. For all intents and purposes it's framed as a normal SATA cable for use with SSD and HDDs. Cracked open the SSD, it's got a resistor absolutely fried. I'm very annoyed that this SATA cable melted $100 of equipment but I guess it's lucky that's all I lost. The HDD is fine and I have everything up and running on Ubuntu the way it was before I started this fiasco. I'm going to save up and get another SSD and try again, this time testing cables as I go.

---

