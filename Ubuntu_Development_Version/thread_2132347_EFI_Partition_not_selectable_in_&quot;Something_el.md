---
title: "EFI Partition not selectable in &quot;Something else&quot;"
date: 2013-04-04
forum: Ubuntu Development Version
---

### Post by sacridex on 2013-04-04
Hello,

I tried to install 13.04 daily(April 2nd) but there was no possibility to create a EFI Partition in "Something else". I was afraid to use "Erase everything and install", because I don't know if it would've worked... If i do not create a new partition table, I could edit the existing EFI Partition(Ubuntu 12.10 is installed) and use it as "Reserved BIOS Space", is this the same? If so, why can't I select it with a new Partition table?

I'm using a Ideapad U410.

---

### Post by grahammechanical on 2013-04-04
I do not have the hardware to test the truth of this but I have seen from posts in other sections of the forum that the live session has to be running in UEFI mode. If the hardware is in BIOS mode then Ubuntu needs to be installed in BIOS mode. If the hardware is in UEFI mode then Ubuntu has to be in UEFI mode. This is not 13.04 specific, in my opinion. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [COLOR=#333333][FONT=Ubuntu]An EFI partition is necessary to install Ubuntu in EFI mode via the manual Ubuntu installer. [/FONT][/COLOR]

[LIST]
[*=left]Since Ubuntu 12.04, it is possible to re-use an existing Windows7 EFI partition (without formatting it). If you use a previous version of Ubuntu, or if you have several installations of GNU/Linux in EFI mode, it is safer to create a new EFI partition EFI.
[*=left][FONT=inherit]An EFI partition can be created via a recent version of [GParted]("https://help.ubuntu.com/community/GParted") (the Gparted version included in the 12.04 disk is OK), and must have the following attributes:[/FONT]
[LIST]
[*=left][FONT=inherit]*Mount point:* /boot/efi (remark: no need to set this mount point when using the manual partitioning, the Ubuntu installer will detect it automatically)[/FONT]
[*=left][FONT=inherit]*Size:* minimum 100Mib. 200MiB recommended.[/FONT]
[*=left][FONT=inherit]*Type:* FAT32[/FONT]
[*=left][FONT=inherit]*Other:* must be located at the start of a GPT disk, and must have a "boot" flag.[/FONT]
[/LIST]
[/LIST]
Regards.

---

### Post by kevpan815 on 2013-04-05
You may need to Turn Off Secure Boot, I had to turn mine off for Beta 2 to run.

---

### Post by kevpan815 on 2013-04-05
Oops, that's supposed to say Secure Boot. Have no way to edit it in the Mobile Browser that I am using right now.

Edit: Nevermind, just found the Use PC Site at the bottom of the Screen.

---

