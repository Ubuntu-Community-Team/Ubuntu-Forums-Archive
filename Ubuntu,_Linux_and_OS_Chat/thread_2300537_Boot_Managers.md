---
title: "Boot Managers"
date: 2015-10-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2015-10-26
I have been using grub since 8.04 and burg since it came out but recently been having a bit of trouble - just wondering if grub is 'old hat' so to speak. I've had a look at EasyBCD and not too keen.  I have two machines, one with eufi, and was wondering how using the bios to choose the os would work?   Not even sure if it works that way.   Is Grub still the default (user wise) bootloader for multiple OSs? (I know is it techie wise as that is what is installed).

---

### Post by oldfred on 2015-10-26
With 8.04, it was grub legacy 0.97.
Now it is grub2 and there are two versions, grub-pc for BIOS boot and grub-efi-amd64 for 64 bit UEFI boot.
I gather burg has not been maintained for years.

If you want a gui type boot manager (not boot loader) you can use rEFInd with UEFI systems.
       Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

Grub is both a boot manager (menu system) and the boot loader for many Linux systems.
UEFI is a boot manager, rEFInd is a boot manager and there are many others.

Some that have issues with proprietary UEFIs that do not really meet the UEFI standard use the UEFI as a boot menu and perhaps one time boot key, manually configure grub into bootx64.efi so system thinks it is booting  a fallback, or use rEFInd.

---

### Post by Quarkrad on 2015-10-26
Many thanks - I will read and install as appropriate.

---

### Post by Quarkrad on 2015-10-27
I'm not sure if this is the right forum for this question &#8211; apologies if it isn't.   I have read some more about converting mbr to gpt and I think I understand enough.  I have backup including Clonezilla images of my partitions.  Are these the correct steps to convert mbr to gpt without losing data?

1.  make a note of beginning and end points (numbers) for each partition (fdisk -l)

2. boot to Live CD and run gdisk

3. delete each partition and create new partition using points/numbers in 1.

4. install rEFInd  (not sure at the moment how to do this. Will read Roderick Smith's docs)

5.  Reboot (entering bios first) &#8211; set defaults (new motherboard so efi booting is default)

6.  Reboot

notes:  

my mbr starts at 2046 so there is room for gpt

my understanding of this process (without losing data) is that you delete existing partitions and recreate in exact positions.

---

### Post by grahammechanical on 2015-10-27
I am concerned that you speak of not losing data in the same sentence as deleting partitions.

All data in a deleted partition is lost. Creating a new partition does not recover the data. The same thing will happen with the whole disk if we create a new partition table. Which is what will happen if you switch from msdos partition table to GPT.

Globally Unique Identifier Partition Table (GPT) is part of the UEFI specification. But it can be used with motherboards that have the BIOS boot system. I have a BIOS boot system. I have one hard disk with msdos partition table and another with Guid Partition Table (GPT). I made the change using Gparted. I created a new partition table on that second hard disk and I used the drop down menu to select GPT instead of msdos. And all the data on that hard disk is not gone, as I expected. No loss there as far as I was concerned.

The machine with a UEFI boot system will most likely already be using a GPT partition table. I also think that if we clone a hard disk and restore it back to the hard disk or even another hard disk of the same size or larger, then we replicate the partition layout that we started with including the data in the partitions. If we clone an msdos partitioned disk and restore it to a GPT partitioned disk we end up with an msdos partitioned disk. It is after all a clone.

Regards.

P.S. as regards your original question. I do not think the UEFI on its own will load the Linux kernel. It will direct the motherboard to look for a boot loader on specific hard disk.

---

### Post by Quarkrad on 2015-10-27
Yes - it worried me, it does not make sense deleting a partition and then creating one and keeping the data.  I am interest in using gparted (that I have use a lot) - when you say '...I created a new partition table on that second hard disk.....And all the data on that hard disk is not gone, as I expected. No loss there as far as I was concerned...' - do you mean that you originally had data on the disk (a single partition?), created a new partition (over the existing?) and none of your original data was lost.  Does this mean I can use gparted to create a new partition table on my sda HD, duplicating what is already there, and no data will be lost?

---

### Post by oldfred on 2015-10-27
You can convert MBR to gpt. But standard ESP - efi system partition is suggested to be first or at least near beginning of drive. I assume there is some limit to how far into drive UEFI driver can read the ESP.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

With gpt you are not supposed to use dd to copy partitions, but can copy entire gpt drive. Something about the additional info gpt partition table has and GUIDs matching. Best to just copy data, not partition structures.

---

### Post by Quarkrad on 2015-10-27
Thank you for your help so far.  It looks like I have converted my hd to gpt &#8211; when I run gdisk /dev/sda -l  it tells me that GPT = present (it was not present) and that MBR = protective (is use to be present).  I have also set my bios boot to uefi mode.  I have created a refind boot usb and I get the refind gui when I boot the pc - I can then boot to ubuntu 14.04.  Once in ubuntu I thought I would install refind using 
$ sudo apt-add-repository ppa:rodsmith/refind
$ sudo apt-get update
$ sudo apt-get install refind

but I had a problem.  I tried it again and got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
refind is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up refind (0.9.2-0ppa1) ...
ShimSource is none
Installing rEFInd on Linux....
The ESP doesn't seem to be mounted! Trying to find it....
// doesn't seem to be on a VFAT filesystem. The ESP must be
mounted at //boot or //boot/efi and it must be VFAT! Aborting!
dpkg: error processing package refind (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 refind
E: Sub-process /usr/bin/dpkg returned an error code (1)

Appreciate help moving forward - I THINK(!) I'm quite close.

---

### Post by oldfred on 2015-10-28
With gpt you need one (or both) partitions for additional information.

With UEFI you must have an ESP - efi system partition. That is a FAT32 formatted partition with the boot flag if using gparted or ef00 if using gdisk. It actually is a very long GUID, but partition tools use shortcust to make it easier. Windows typically makes it 100MB, but we normally suggest 200 to 500MB. 

With BIOS and gpt you need a tiny 1 or 2MB unformatted partition with the bios_grub flag or with gdisk code ef02. That is where grub puts core.img that in MBR is in the sectors after the MBR. With gpt there is no space after its protective MBR. Gpt only has protective MBR with one entry saying it is gpt partitioned so older partition tools will see drive as partitioned and not automatically overwrite it.

All my new drives for last several years, even when still only BIOS were gpt partitioned since I was not also installing Windows. Then drive could be used in older or newer system without total repartitioning. But Windows only boots from gpt with UEFI, so a Windows drive cannot be converted to gpt if BIOS booting.

---

### Post by yoshii on 2015-10-31
This is a slightly different issue but I use GRUB4DOS as my boot manager.  I use an MBR type system and I got used to editing the menu.lst from Puppy Linux installations.  So I kept using GRUB4DOS even with Ubuntu.  It works out because GRUB4DOS is similar enough to grub2 for loading boot images.  I send it the right kernel commands and it pretty much ignores Ubuntu's grub which I like because I find Ubuntu's Grub2 confusing to configure.  GRUB4DOS lets you edit a menu.lst file to get a custom menu prompt and it's fairly easy to learn.  The other nice thing is that it displays the text of the loading process instead of an animation or blank screen.  

The downside is that I can't seem to find support for GRUB4DOS outside of Puppy Linux except for within Windows DOS which I definately don't want to do.  But for MBR multiboot systems of linux, it's pretty nice.

---

### Post by oldfred on 2015-10-31
Grub4dos uses the same structure as grub legacy.
You can easily translate a menu.lst to grub.cfg. When grub2 first came out it automatically convert it, not sure if it still has that capability or not.
Main difference are partitions with grub started at 0, but with grub2 start at 1, so hd0,0 is then hd0,1.
And grub2 often includes msdos or gpt in (hd0,gpt1), so it knows if MBR or gpt.
It also uses {} to define the boot stanza.
You can in grub remove the quiet splash setting so you see boot process.
And you add your own boot stanzas in 40_custom.
       [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

