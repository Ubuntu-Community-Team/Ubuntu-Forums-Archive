---
title: "UEFI and 15.10 compared to 14.04.3"
date: 2015-09-14
forum: Ubuntu Development Version
---

### Post by fjgaude on 2015-09-14
I notice a strange situation trying to dd to a flash drive 15.10. It seems it makes two partitions on the drive, one efi and the other the main file.

Now trying to re-format such a flash drive failed using disks and gparted.

Did this situation start the discussion on how to make flash drives from .iso files?

Any comments from anyone?

Thank for any thoughts!

---

### Post by QDR06VV9 on 2015-09-14
@fjaude
To reformat your flash drive or USB you need to boot to a Gparted disk then insert your bad drive and then format it.
if I understood you correctly.
If not kindly dismiss this.
Regards

---

### Post by fjgaude on 2015-09-14
After **dd**ing 15.10 to the flash drive I cannot using gparted or disks reformat the flash. I don't know what a bad drive is. <smile>

---

### Post by QDR06VV9 on 2015-09-14
[COLOR=#000000]you need to boot to a Gparted disk  as in download a iso burn to disk then boot to gparted[/COLOR]
[COLOR=#000000]Insert your bad USB and then format. Assuming it is a USB.
See this thread
[/COLOR]http://ubuntuforums.org/showthread.php?t=2294578

---

### Post by howefield on 2015-09-14
> **fjgaude said:**
> Thank for any thoughts!

Try creating a new partition table. Then format as required.

---

### Post by fjgaude on 2015-09-14
> **howefield said:**
> Try creating a new partition table. Then format as required.

Did that but it still didn't work... I'll do some study on just how UEFI works and maybe get a feel for what I'm doing wrong. Thanks!

---

### Post by tista on 2015-09-14
@fjgaude,

**gdisk** could work to write partition-table?

Regards.

---

### Post by fjgaude on 2015-09-14
> **tista said:**
> @fjgaude,

**gdisk** could work to write partition-table?

Regards.

Okay, tista, thanks, will try it.

---

### Post by fjgaude on 2015-09-17
Well, after much study, I think I understand UEFI and its advantage: faster boots, by two to one through parallelism. Ubuntu UEFI fully installed booted in about 6 seconds, whereas 14.04.3 in 12, which is BIOS loaded. (I finally did get a flash drive able to install a 15.10 .iso and installed onto a partition of my main box.

Anyone know why 14.04 is not UEFI. It seems in its early days it was.

Thanks for everything.

---

### Post by oldfred on 2015-09-17
I am running original 14.04 in UEFI mode, even though it now says 14.04.3 with updates. 
Kernel is still original not enablement stack.

       Support for UEFI appeared in 11.10, but has become more reliable with each update. 
Support for UEFI SecureBoot appeared in 12.10 with grub2 2.00, and then 12.04.2.

---

### Post by fjgaude on 2015-09-17
What I would need is an early 14.04 that is UEFI and install it along with a huge amount of updates.

Thanks, oldfred, for all the times you have come to our aid.

---

### Post by mc4man on 2015-09-17
you can get any 14.04 you want from here (or anything else ubuntu wise
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by fjgaude on 2015-09-18
Cool, sweet! And thanks, I'll bookmark the site!

---

### Post by sudodus on 2015-09-18
Your current problem seems solved, but I would like to add a method, that makes it possible to create a new partition table in drives, that are not accepted by gparted and similar tools: Wipe the first megabyte!

It can be done 'with a safety belt' using [mkusb and its wipe menu](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device).

---

### Post by fjgaude on 2015-09-18
> **sudodus said:**
> Your current problem seems solved, but I would like to add a method, that makes it possible to create a new partition table in drives, that are not accepted by gparted and similar tools: Wipe the first megabyte!

It can be done 'with a safety belt' using [mkusb and its wipe menu](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device).

Okay, and thanks! I see the issue. I see the issues. I will likely continue to use** dd **as I have for years, but the prep of the flash drive is something I'll be careful about.

**mkusb** such is well made. Thanks to those who did all the work, sudodus?

---

### Post by fjgaude on 2015-09-23
After trying about four UEFI installs and then trying to reuse the USB flash drives I can see why the folks dropped UEFI version in 14.04.2 and beyond. That's when I saw the advantages to using **mkusb** in wiping the first megabyte of the drive, where the EFI lives. <smile>

But I don't understand, maybe why, they have brought it back in 15.10. Likely has something to do with 14.4 being LTS and 15.10 is short lived?

With the fast SSDs many of us now use boot time is no longer much of an issue!

Thanks again to those that brought us the flash drive issue.

---

### Post by sudodus on 2015-09-24
I don't understand what you mean by "I can see why the folks dropped UEFI version in 14.04.2 and beyond". The Ubuntu iso files of 14.04.2 and beyond can be used to run Ubuntu live and to install Ubuntu in the new UEFI mode as well as in the traditional BIOS mode.

When a computer is delivered with Windows nowadays, it is installed in UEFI mode. If we want to install Ubuntu alongside Windows, we 'have to' do it in UEFI mode too. OK, it is possible to install Ubuntu in BIOS mode, but then we must go to the BIOS/UEFI system and switch mode every time we want to switch between Ubuntu and Windows, and it is not very convenient.

Unfortunately some UEFI systems are not made according to the UEFI standard, and this makes it difficult to install Ubuntu and other linux operating systems.

---

### Post by fjgaude on 2015-09-24
Well, with my research and experimentation I've determined that only the release of 14.04 has EFI data. 14.04.1, .2,  and .3 do not. If you can determine otherwise please let me know. 

To come to my conclusions I downloaded all four .iso files from the Ubuntu Release Index site. I have them on my main drive. Used your mkusb to put the .isos onto flash drives.

I think because 14.04 is LTS the producers figured that UEFI was causing too much of a hassle with trying to reuse flash drives, the first 1meg space for the EFI software. Do you know something I don't?

---

### Post by sudodus on 2015-09-24
I can boot the amd64 desktop versions of all 14.04 LTS and the point versions .1, .2 and .3 in UEFI mode. The UEFI setup may be changed, but not much. As a matter of fact, I find 14.04.2 and 14.04.3 more stable in UEFI mode than the previous versions.

1. It is possible for me to boot pendrives made from all *buntu (standard Ubuntu, Kubuntu, Lubuntu, ..., Xubuntu) desktop iso files in persistent live mode (also the i386 versions, where the UEFI capability comes from mkusb). So this 'does not count' ;-)

2. All live-only, ***cloned***, current *buntu ***desktop*** systems from ***amd64*** iso files boot in both UEFI and BIOS mode, but the i386 live-only (cloned) versions only boot in BIOS mode, and systems installed with debian installers (mini.iso, Ubuntu Server, Lubuntu alternate) work only in BIOS mode. Maybe you are comparing amd64 (64-bit) systems with i386 (32-bit) systems or with systems installed with debian installers?

***Edit:*** Installed systems behave like the live-only systems concerning UEFI and BIOS.

---

### Post by fjgaude on 2015-09-24
Only use 64-bit systems here... when I look at the files in each of the .iso I only see EFI folders for 14.04, not 14.04.1, .2, or .3. I see it in 15.10 and have that installed on two partitions. Right now each of my 14.04.3 partitions are for work and I don't have time to start over with one of them.

It is very interesting what you say, and I take it seriously. I'll see as time goes by if I can agree with your findings. Thanks again.

---

