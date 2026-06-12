---
title: "[SOLVED] Copying system to a new computer."
date: 2015-07-05
forum: Ubuntu, Linux and OS Chat
---

### Post by pingaan on 2015-07-05
Hi,

What complications might I run into? This isn't something that is relevant at this moment but hopefully soon. 
I guess the actual question is if Ubuntu and booting up has alot of issues recognizing 100 % new hardware? 
Should I do a fresh install?

Regards.

---

### Post by Lars Noodén on 2015-07-05
I'd do a fresh installation if it's new hardware, but port over the configurations and data.  This would be a good opportunity to test (or deploy) a backup and recovery method.

---

### Post by Bucky Ball on 2015-07-05
*Thread moved to **Ubuntu, Linux and OS Chat**.*

... as this is currently theoretical as you haven't done it yet. Consequently, you will get a lot of opinions as there is no definitive answers. 

Because of the fact this is currently theoretical, your questions are almost impossible to answer with any accuracy. What complications you might right in to? Build or buy a machine with parts that are not Linux compatible, lots. Build or buy one with lots that are, none or few. Research into the hardware is key. 

Ubuntu has no issues recognizing new hardware when moving an existing install from one machine to another. The drivers are there in the Ubuntu kernel already. The main problems you may have, and another thing to add to the many or few possibilities for your first question, are graphics and wireless card drivers if the graphics and wireless card are different from the ones in the other box. 

I use [Clonezilla]("http://clonezilla.org/") for moving entire installs. A clean install, as suggested, is your other option. I have no idea if you are running 15.04 for a specific reason and don't mind upgrading once or twice a year, but if you do a reinstall you might consider a long-term support release. 14.04 LTS is supported until 2019. 15.04 til January 2016. Good luck. :)

---

### Post by monkeybrain20122 on 2015-07-05
I always do that. When a new Ubuntu comes out I install it on an external drive, take a month to test it and customize it to my liking, when everything works then clone it and restore it to my internal hard drive. Recently I did that with Ubuntu 15.04 and restored the same system to two different computers (totally different specs and partition layouts).  I use fsarchiver [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)  At the same time I cloned 14.04 and restored it to another external drive as a portable and just in case I need to downgrade after 14.04 eol if 15.10 turns out to be as bad as 14.10 :)

The advantage of fsarchiver over clonezilla is that it copies the file system instead of sector by sector so it is not restricted by low level stuffs on the drive, hence more flexible. It is very fast and can do live cloning (cloning when computer is in used) It can be restored to any partition as long as it is big enough to hold the content, Clonezilla has this stupid requirement that the partition to restore to must be at least as big as the original one even if the original was mostly empty. This is important if you try to repartition the drive or restore to a computer with different partition layout. With clonzilla you have to first shrink the partition to be cloned using gparted, which can be very slow and potentially risky.

Things to look out: 
1. proprietary graphic driver, obviously if two computers have different graphic cards then it won't work if you try to move a system with incompatible proprietary driver, so have to remove such driver before you clone if this is the scenario. If you use only open source driver then it can boot anywhere as long as the card is Linux compatible 
2. UEFI, it may work perhaps with some mugging around, but better to use legacy mode, it is guaranteed to work 
3. may need to reinstall grub. 
4. need to edit fstab for the correct uuid for the swap partition since you can't move swap along with this method.

---

### Post by oldfred on 2015-07-05
I believe in new installs, and if you copy /home & list of installed apps you have most of your old system & configurations.
My backup is to restore to same system, but with a new install.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

With my new system, I did go from BIOS to UEFI. But I had converted most of my drives to gpt as I still had XP on MBR drive. 

UEFI is newer and does have some advantages. But it is not yet as well understood by many  as BIOS had been around since the first IBM PC in the 1980's.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by monkeybrain20122 on 2015-07-05
I may be missing something. But unless you have a drive bigger than 2 TB I really don't see what are the advantages of GPT that oldfred often links to here. Sure you can have as many primary partitions as you want but why would any normal user need more than 4? And in any case you can use an extended partition with as many logical partitions as you want. There are people who multiple boot 4 or 5 OSes (and more) with extended partitions.

---

### Post by kansasnoob on 2015-07-06
> **monkeybrain20122 said:**
> I may be missing something. But unless you have a drive bigger than 2 TB I really don't see what are the advantages of GPT that oldfred often links to here. Sure you can have as many primary partitions as you want but why would any normal user need more than 4? And in any case you can use an extended partition with as many logical partitions as you want. There are people who multiple boot 4 or 5 OSes (and more) with extended partitions.

Most truly "new" hardware is now UEFI only, I haven't seen much truly "new" hardware that has the ability to still boot in either legacy or UEFI mode, so GPT + UEFI is the latest and greatest thing. Although there are still numerous kinks to work out before I'd personally consider it "the greatest" ;)

I recently built 11 budget boxes, some Win + Ubuntu dual-boots and some straight Ubuntu, but all UEFI only and they worked out well ................... but multi-booting more than one Linux distro is more than a bit of a nightmare.

---

### Post by pingaan on 2015-07-07
Wow! Thanks for all the thought-through answers.. I will save this thread and probably give life to it again once the actual upgrade will take place!

Thanks a ton!

---

### Post by monkeybrain20122 on 2015-07-07
> **kansasnoob said:**
> Most truly "new" hardware is now UEFI only, I haven't seen much truly "new" hardware that has the ability to still boot in either legacy or UEFI mode, so GPT + UEFI is the latest and greatest thing. Although there are still numerous kinks to work out before I'd personally consider it "the greatest" ;)

I recently built 11 budget boxes, some Win + Ubuntu dual-boots and some straight Ubuntu, but all UEFI only and they worked out well ................... but multi-booting more than one Linux distro is more than a bit of a nightmare.

Well if you have no choice then of course you have to do gpt + UEFI. But that is not an argument for choosing UEFI and GPT over legacy when you DO have a choice. So that is not really an advantage. :) And since multibooting more than one Linux poses a problem it is definitely a disadvantage.

---

### Post by oldfred on 2015-07-07
I am multi-booting several Ubuntu's on my UEFI machine. 
The main issue is all grub installs are to sda. 

I know I told it to install grub to sdb's efi partition and it even said during install, installing grub to sdb. But it overwrote the efi partition on sda.
If same version of grub, all that really changes is the tiny grub.cfg in /EFI/ubuntu that is a configfile to the actual grub.cfg and which partition it refers to. I have backup of that grub.cfg to restore my default version.

---

### Post by Dennis N on 2015-07-07
> **oldfred said:**
> I am multi-booting several Ubuntu's on my UEFI machine. 
The main issue is all grub installs are to sda. 

I know I told it to install grub to sdb's efi partition and it even said during install, installing grub to sdb. But it overwrote the efi partition on sda.
If same version of grub, all that really changes is the tiny grub.cfg in /EFI/ubuntu that is a configfile to the actual grub.cfg and which partition it refers to. I have backup of that grub.cfg to restore my default version.

All true. And just think that with the above situation and UEFI, the user can change which system to boot by just using a terminal and edit a file /EFI/Ubuntu/grub.cfg  and change the UUID into what you want. While with BIOS, you cannot change the MBR contents by editing a file (there is no file in there). So with MBR, if you wanted to boot to grub in a different OS - you need to reinstall grub from that other OS. 

I also find GPT superior to MBR setups. A real partition table addressing all partitions and has a backup. No logical partitions hack needed.

---

### Post by monkeybrain20122 on 2015-07-07
> **Dennis N said:**
> All true. And just think that with the above situation and UEFI, the user can change which system to boot by just using a terminal and edit a file /EFI/Ubuntu/grub.cfg  and change the UUID into what you want. While with BIOS, you cannot change the MBR contents by editing a file (there is no file in there). So with MBR, if you wanted to boot to grub in a different OS - you need to reinstall grub from that other OS. 

I also find GPT superior to MBR setups. A real partition table addressing all partitions and has a backup. No logical partitions hack needed.

Well if your use case involves frequently changing boot order I suppose that is an advantage, though through my lack of imagination I really can't understand why anyone would want to change boot order every few days. :)  If it is an one off thing then reinstalling grub is really not that big a deal, you still only have to type two commands into the terminal. 

 But OP asks about moving installations/partition around, gpt seems inflexible and extra works will be involved.

---

### Post by Dennis N on 2015-07-07
Well, it's not about changing the boot order in a grub menu, but what grub menu you get on startup. When you install a new OS, EFI/ubuntu/grub.cfg is overwritten. This is about restoring the previous version of this file.

UEFI boot manager starts the boot loader grubx64.efi or shimx64.efi in the EFI system partition. EFI/ubuntu/grub.cfg in that partition gives the boot loader the partition and directory for the configfile (also named grub.cfg) to use for the grub menu. 

So there are two grub.cfg files here which serve different purposes.

---

### Post by monkeybrain20122 on 2015-07-07
> **Dennis N said:**
> Well, it's not about changing the boot order in a grub menu, but what grub menu you get on startup. When you install a new OS, EFI/ubuntu/grub.cfg is overwritten. This is about restoring the previous version of this file.



In MBR you can just install grub into the partition (instead of drive) or not install grub at all when you install the new OS (fedora, e.g has an option of not installing bootloader) so the original grub doesn't get overwritten. I have had installed 3 or 4 OSes on the same drive this way (when I still had time to play with different distros) and I never have the original grub overwritten (expect by accident :)) The only distro that refuses to cooperate is OpenSuse but I think it is its problem.

---

### Post by Dennis N on 2015-07-07
> In MBR you can just install grub into the partition (instead of drive)
Absolutely. I still do it myself on the our non-UEFI computers that still use an MBR and MSDos Partition Table.

---

### Post by oldfred on 2015-07-07
From the live installer in live mode, you can install without installing grub.

 This launches the installer program (Ubiquity) with an option (-b) to not install a boot loader from live installer in live mode:
In the Terminal window, type ubiquity -b.

---

### Post by pingaan on 2016-01-07
Alright, so what I did was simply installing the drive into the other computer and it booted up like it had never seen nyany other hardware... In other words; it worked flawless and I didn't run into any errors at all...

Impressive Ubuntu!!

---

