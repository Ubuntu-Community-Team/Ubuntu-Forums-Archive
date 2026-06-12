---
title: "Install wipes efi partition"
date: 2023-03-26
forum: Ubuntu Development Version
---

### Post by jallain on 2023-03-26
I tried to install on actual hardware and the installer kept crashing. Finally got to where I could get the installer to run. After doing nothing for essentially forever, I reboted. That was when I noticed that my boot menu was not there. I booted up partiion magic and discovered that my efi partition was blank. It was actually formatted because it had a new UUID. I had to edit the fstab files on my other installations to get them to boot. I tried a new download of the daily build and the results were the same.

---

### Post by zebra2 on 2023-03-26
I've done six new installs of the 23.04 ISO in the past week with no problem.  
Best to use a USB created with the Ubuntu Startup Disk app.  I seems to me that the Ubuntu Installer will only offer as available the boot partitions required by the Bios configuration.  
Using the Startup disk installer choose "something else" at the install options.  The first partition on the disk should be a 256 meg with the  EFI (ESP) flag set after the partition  is created. You don't format this partition because the installer will properly format it for you.  The second partition could be a SWAP partition if you prefer this to a "swapfile".  Third partition should be / (root).  The rest of disk /Home.

All of this is just a suggestion but it will make a reinstall easy if needed. On a reinstall you go back to the partition table and only  format the /root partition.  Reuse the /Home but don't format. This way all of your software settings are preserved.

If you can get this right you will have a easy process and you can try out anything else you dig up later.

---

### Post by jallain on 2023-03-26
I use Ventoy to boot different distros. They all work well. Even All flavors of Ubuntu. Do I understand that 23.04 will format my efi parition as part of the install process? That is not acceptable as I have two other distros on my disk. Please tell me I'm misunderstanding what you said.

---

### Post by grahammechanical on 2023-03-27
> Using the Startup disk installer choose "something else" at the install  options.  The first partition on the disk should be a 256 meg with the   EFI (ESP) flag set after the partition  is created. You don't format  this partition because the installer will properly format it for you.

In my opinion we need to direct the installer to install the boot files into the EFI system partition. If you see a checkbox labelled "format" DO NOT tick that checkbox. Otherwise the installer will indeed format the EFI system and remove any EFI boot file s for other operating systems. With the "format" checkbox unchecked the installer will only put the Ubuntu boot files into the EFI system partition. Existing Ubuntu boot files will be overwritten. This is not a problem. The boot files for non-Ubuntu operating systems will be left untouched. I have tree different installs of Ubuntu on my drive and this is how I did it.

By the way, we do not get a boot menu (Grub) if we have only one operating system on the drive. I am not sure if you have other OS on that drive. Also, my EFI system partition is 537 MB in size and is formatted as FAT 32. A machine with Windows on it will have the Windows boot files in a FAT32 EFI system partition. We do not change that even if the only OS are Linux.

Regards

---

### Post by zebra2 on 2023-03-27
@grahammechanical :
My experience is parallell to yours.  On three systems I have EFI/ESP partitions of 256meg, 269meg and 1gig.   All created by the installer with some help from me.  the 269meg partition was made from a deleted 14meg bios/boot joined to a 256meg esp.  I don't know how I ended up with the 1Gig esp.  I believe the Ubuntu installer is looking at the bios of the machine and doing what it is programmed to do.  I have grub setup to boot multiple partitions but they are ignored. It won't even pickup a Puppy Linux install in 40_custom.  They most likely won't have all of this fixed at release date.  So far as the OP is concerned, he may have chosen the wrong version to meet his purpose.  What he has posted doesn't belong in this section of the forum. In my opinion.  I do have a Puppy USB made from Rufus that boots.  I get the boot menu from F12 key on boot. 
PS: Good to hear from you. Been a while.

PS #2: I think the OP is correct though if the installer doesn't like our choices made it will either delete or reformat to suit itself.

---

### Post by IanW on 2023-03-30
The Windows installer is no better (He says while wiping a grand total of _thirteen_ EFI partitions off an _unrelated_ SSD after a failed Windows install attempt)

---

