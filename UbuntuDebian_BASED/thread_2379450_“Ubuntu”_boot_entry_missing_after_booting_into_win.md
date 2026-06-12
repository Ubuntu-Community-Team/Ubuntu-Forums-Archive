---
title: "“Ubuntu” boot entry missing after booting into windows"
date: 2017-12-05
forum: Ubuntu/Debian BASED
---

### Post by grafkazu on 2017-12-05
[COLOR=#242729][FONT=Arial]I've been using Windows 10 primarly but after using a Mac at the office and having a Linux server I've installed Zorin OS as a dual boot option because it's so much better for development than Windows, obviously xD[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I don't even need Windows anymore if it wasn't for the Adobe Creative Cloud which is not supported on Linux for some reasons.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Everytime I boot into Windows my "ubuntu" boot entry is replaced by "Windows Boot Loader" even though I've disabled secure boot and hibernation, which means I have to boot into my USB drive, install boot-repair just to be able to boot into my Zorin OS.

I'm getting an error everytime I try to run boot repair which says "ESP-locked", so I looked it up.
1. I've unchecked the boot flag using gParted.
2. Launched Windows
3. Mounted the boot partition
4. Deleted "EFI/ubuntu"
5. Launched Zorin OS live version from stick

I then either set the boot flag back before running boot-repair or just ran straight up boot-repair. Nothing worked and I still got the same error.

Here are some logs:
[COLOR=#222222][FONT=Verdana]
[FONT=arial][http://paste.ubuntu.com/26104193/](http://paste.ubuntu.com/26104193/)
[/FONT][/FONT][/COLOR][/FONT][/COLOR][FONT=arial]
[http://paste.ubuntu.com/26104264/](http://paste.ubuntu.com/26104264/)

[/FONT][[FONT=arial]http://paste.ubuntu.com/26104330/[/FONT]]("http://paste.ubuntu.com/26104330/")

[COLOR=#242729][FONT=Arial]I'm using a ASRock Z77 Performance motherboard. I also reflashed by BIOS because I tried a Hackintosh before but never got it to work and had many Clover boot entries which I wanted to get rid of xD[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Does anyone had a similar problem and might be able to help me?[/FONT][/COLOR]

---

### Post by oldfred on 2017-12-05
Moved to other OS, as not Ubuntu.

You have Windows in UEFI boot mode.
You have Zorin installed in BIOS boot mode.
Your sda, sdd & sdf are gpt partitioned but sdb, sdc & sde are BIOS(msdos) partitioned.

Grub installed to the protective MBR on a gpt partitioned drive should have a bios_grub partition. It says it cannot find the rest of grub, so not current boot loader.
I prefer to use gpt on all drives and include both the ESP and bios_grub partitions even if not currently used, but for future use if needed, so I do not have to then totally redo drive.

You also show burg, which is now a very old BIOS boot loader. If you want graphical boot (only with UEFI) use rEFInd.
 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) 


I have found having a flash drive plugged in can change drive order. While system still should boot with UUID & UEFI with GUIDs, I still sometimes have issues. I have in past skipped SATA port and my sdb drive changes in grub from hd1 to hd2 when flash drive plugged in. Flash drive was becoming in UEFI as skipped SATA port enumeration. 

With UEFI, the boot flag must only be on the ESP partition.
With BIOS boot flag must be on primary NTFS partition with boot files.
Grub does not use boot flag.

ESP locked is often corruption. Some run chkdsk from Windows.
       Must be unmounted, or use live installer only.
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

In some cases, users have had to fully back up ESP, erase FAT32 partition, create brand new FAT32 partition and add boot flag to make it ESP (or code ef00 in gdisk). And restore files. But often you have to run efibootmgr to update UEFI boot entries as GUID has changed.

---

### Post by grafkazu on 2017-12-05
Why was Zorin installed in BIOS boot mode though? The Stick is shown as "UEFI: SANDISK" in my boot entries.

I can't change the partioning at the time because all of my drives are close to full and I have no where to store it temporarily.

Is there a guid on how to gpt and include ESP and bios_grub?
I never worked with a dual boot system before xD

---

### Post by howefield on 2017-12-05
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2017-12-05
OOPs, forgot to move it. 

You can review the link in my signature for summary details on UEFI install,  and its many links to more details on any part of UEFI install you do not understand.

---

