---
title: "Pop OS / Windows 7 Dual Boot Trouble - No Operating System Found"
date: 2023-04-08
forum: Ubuntu/Debian BASED
---

### Post by arius88 on 2023-04-08
I hope this is the right place to go for support on this. 

Someone recently gave me a Lenovo ThinkCentre with Windows 7 on it. 
I'm not a fan of Windows, but there's a program installed on there that I don't want to lose, so I decided to make it a dual-boot machine.

Went through the POP OS install method with some help from a person on youtube. Everything seemed to be going pretty well. I set up the partitions, created a username, etc. 
But when it got to the reboot stage, everything went wrong. Instead of booting into Pop OS, it gave me the following error:

No Operating system found. Press any key to repeat boot sequence.

(Pressing any key just results in the same error over and over, as one would expect.) 

That was two days ago. I somehow figured out how to launch the installation medium again, and, after a bit of work and resolving new random errors, managed to get through the whole process again, and got the same result. Reboot. No operating system found. 

I have no idea what to do next. The upsetting part is that I also can't figure out how to get Windows to launch, even though I'm sure it's still on the hard drive somewhere, and I actually need to use it today.

Please help!
Thanks,
Arius

Possibly relevant: I believe the machine used to work in a bank and may have some sort of security thingies on it to prevent tampering.

---

### Post by MAFoElffen on 2023-04-08
> **arius88 said:**
> I hope this is the right place to go for support on this. 
> **cofeecat said:**
> The first two main sections of the forum - Ubuntu Official Flavours  Support and Ubuntu Specialised Support - are reserved for the official  flavours of Ubuntu, but you are welcome to post PopOS questions in the [Ubuntu/Debian Based]("https://ubuntuforums.org/forumdisplay.php?f=452") sub-forum. 
One of the Forum Admins or Moderators will probably move this thread to there...

If you run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info") from a LiveUSB, and post the URL of where it uploads to a PasteBin.... That will at least give you a chance that someone can see what you have hardware wise and system wise. I made sure that would run for other Linux Distro's, especially derivatives of Ubuntu.

EDIT: I will try to follow this and tell you what I see in that report.

---

### Post by jeremy31 on 2023-04-08
Moved to Ubuntu/Debian based

---

### Post by arius88 on 2023-04-08
Great, thank you!

---

### Post by oldfred on 2023-04-08
Really need to see report.
But Windows 7 was usually BIOS/MBR, and then booted from the MBR.
But PopOS uses SystemD boot for UEFI booting by default, but some do have grub. Not sure it does BIOS installs?

Some newer UEFI capable systems had Windows 7 either in BIOS or UEFI mode. But Microsoft required vendors to install Windows 8 in UEFI mode to gpt partitioned drives starting in 2012. So is system newer than 2012? Often, if older, then a lighter weight flavor is recommended.

Depending on if BIOS/MBR, or UEFI/gpt the suggested fixes are different. 

Note that Windows 7 is obsolete and should not be used to connect to Internet. Only use for local applications.

---

### Post by arius88 on 2023-04-09
Gonna try to get that report, but it would help to know what the heck a pastebin is please!

---

### Post by arius88 on 2023-04-09
Okay! Report is here: [https://paste.ubuntu.com/p/836MxYgk6x](https://paste.ubuntu.com/p/836MxYgk6x)

The one thing that stuck out to me as potentially helpful is "EFI variables are not supported on this system." I assume that is somehow related to the UEFI (no idea what that is) BIOS thing?

I gotta say, this Report-amabob thingy is amazingly useful. Mad props to whoever came up with it.

---

### Post by arius88 on 2023-04-09
> **oldfred said:**
> Really need to see report.
But Windows 7 was usually BIOS/MBR, and then booted from the MBR.
But PopOS uses SystemD boot for UEFI booting by default, but some do have grub. Not sure it does BIOS installs?

Some newer UEFI capable systems had Windows 7 either in BIOS or UEFI mode. But Microsoft required vendors to install Windows 8 in UEFI mode to gpt partitioned drives starting in 2012. So is system newer than 2012? Often, if older, then a lighter weight flavor is recommended.

Depending on if BIOS/MBR, or UEFI/gpt the suggested fixes are different. 

Note that Windows 7 is obsolete and should not be used to connect to Internet. Only use for local applications.

I appreciate the warning about connecting Windows 7 to the internet. My instinct was not to do that, but the confirmation helps. 

Just FYI I have to idea what any of the following computer jargon means:

MBR
SystemD
UEFI
grub
gpt

And I have no idea how old/new the system is.

---

### Post by arius88 on 2023-04-09
Oh! Also the current boot mode is legacy, so i assume that means it's booting from BIOS? (Got this from an article, not really clear what that means.)

---

### Post by oldfred on 2023-04-09
If you scroll down to the bottom of the link in my signature is a list of acronyms and links to details on what they mean.

From that link:
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by arius88 on 2023-04-09
> **oldfred said:**
> If you scroll down to the bottom of the link in my signature is a list of acronyms and links to details on what they mean.

From that link:
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

I appreciate, that, thank you. I did google a couple of the terms after the fact. I have pretty severe brain fog due to CFS/ME, so I'm pretty easily confused.

What I've gathered after googling and re-reading your earlier message, is that it may be the case that Pop OS requires me to have a UEFI system, and mine is Legacy BIOS.
I'm trying to google work-arounds but having trouble finding anything useful and comprehensible (to me) that feels safe to try. 
Suggestions would be appreciated. I'm completely in love with Pop OS and really want to make it work if possible.

---

### Post by arius88 on 2023-04-09
I think I might have muffed up the install by following a youtuber.  They said to make a boot partition, but i think this was wrong and that I need that partition to be a swap partition. I'm trying to change it now, but the "erase and install" button is greyed out for no obvious reason and won't work.I've tried making various changes and nothing will make the button turn red like it's supposed to be. I also can't format the newly designated "swap" partition even though I'm pretty sure the install will fail if I don't, because there are leftover Pop files or something from the previous time I tried to install it. 

Q: does the format matter? It wants me to do ext4 for some reason, The youtuber advised Fat32 but the installer insists this is the wrong format. 

Update: I just noticed that when I hover over the root partition, it says "invalid filesystem for root," despite the checkmark. I tried switching it to every available filesystem - Fat32, ext4, Fat16, etc - and they are all invalid.
Further update: I formatted the linux root partition as ext4 and now the error is gone, but the "Erase and Install" button is still greyed out despite no errors and two checkmarks. Here's what I have right now in terms of partitions:

1. 512 MB swap partition (for Pop)
2. 100 MB ntfs partition (for Windows 7)
3. 285 GB ntfs partition (for Windows 7)
4. 200 GB ext4 root partition (for Pop)

---

### Post by oldfred on 2023-04-09
Never installed POP.
But it defaults to SystemD boot which is an UEFI boot loader, but I believe it can use grub.
With UEFI it needs either a larger ESP - efi system partition or another partition for some of its boot files. Not sure it than can be done with BIOS/MBR systems.

Arch often has the best info. Quick look makes it seem difficult to use with BIOS, but can be done.
[https://wiki.archlinux.org/title/systemd-boot](https://wiki.archlinux.org/title/systemd-boot)
[https://wiki.archlinux.org/title/Systemd-boot#Installing_the_EFI_boot_manager](https://wiki.archlinux.org/title/Systemd-boot#Installing_the_EFI_boot_manager)

Are you sure you want POP os?
Perhaps a Ubuntu flavor and light weight for older systems?
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

[https://support.system76.com/articles/difference-between-pop-ubuntu/](https://support.system76.com/articles/difference-between-pop-ubuntu/)

---

### Post by arius88 on 2023-04-09
[QUOTE=oldfred;14138272]Never installed POP.

Are you sure you want POP os?
Perhaps a Ubuntu flavor and light weight for older systems?
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
/QUOTE]

I'm hoping I can resolve the issue with the "Erase and Install" button being greyed out and then try one more install before giving up on Pop. 

And yes, I'm sure I want Pop. I've tried a ton of different ubuntu operating systems and desktop environments over the last few years, and Pop is the only one I've ever really loved. 
I found it very easy to customize it exactly the way I wanted, and it's beautiful. (If I'm going to look at something every day, I want it to look good.)
I'm willing to settle for a different OS if I can't get Pop to work, but I haven't quite reached that level of despair yet. 

Thanks for the lightweight suggestions. That helps me narrow things down a bit if I have to bail on Pop. 
I'm thinking Lubuntu might be the choice for me. I used that before and found it very fast and good on an old machine, although I was very unhappy with the aesthetics. Hopefully I can tweak it to taste.

---

### Post by arius88 on 2023-04-09
Update: giving up. Gonna try Lubuntu. Thanks for all the help, anyway!

---

### Post by arius88 on 2023-04-09
Turns out I could use a little help with the Lubuntu install. I've got two options here: replace a partition, and manual partitioning. I've already created a blank ext4 partition and a swap partition on the drive when I tried to install Pop. It is totally unclear whether clicking "Replace a Partition" will allow me to choose which partition I want to install Lubuntu onto, or simply format my entire hard drive. I clicked the Manual Partitioning button and saw all my partition sitting there with no real option to do anything that I could detect, and the "Next" option greyed out. So now I'm stuck again. I can't move forward without risking deleting the Windows system I need. Anybody know what happens if I click Replace a Partition?

UPDATE: NVMD! FIGURED IT OUT! Turns out pressing the Replace a Partition button is pretty safe and DOES allow me to select which partition I want to put Lubuntu on. Phew.

Further Updates:

1. The Lubuntu install was quick and easy aside from the above-named ambiguity. I updated the software and everything seems to be running great so far.
2. However, I have two new issues. The first is minor: I have 3 DEs to choose from: lxqt, Lubuntu, and OpenBox. When I enter my password to log in, Lubuntu takes 10 seconds to load, lxqt takes about 4, and OpenBox just freezes and I have to manually power down my computer. I probably don't even want to use OpenBox, so I don't particularly care if this gets resolved. 

The bigger issue is that now I CANNOT GET WINDOWS TO BOOT. I managed to find an option to load Windows in a startup menu, but when I click on it, it says "Windows failed to start. A recent hardware or software change might be the cause." It then asks me to install a Windows 7 system disk, which I don't have. At the bottom it says "Info: The boot selection failed because a required device is inaccessible."

Any idea what the problem is, or how to fix it?

---

### Post by oldfred on 2023-04-09
Grub only boots working Windows.
And with one MBR, you have to boot Windows from grub or temporarily replace grub with Windows boot loader, fix Windows & restore grub.
You probably need your Windows repair/recovery disk to fix Windows.

Probably best to start a new question as title not correct now for new issue. In Windows sub-forum, but since obsolete Windows not sure how much help you will get.
Better to ask in Windows forum, but again an obsolete Windows.

---

