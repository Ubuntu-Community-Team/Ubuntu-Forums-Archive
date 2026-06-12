---
title: "Installing Linux on MicroSD Cards?"
date: 2014-01-16
forum: The Cafe
---

### Post by neu5eeCh on 2014-01-16
So, I've been investigating this and discovered [the following]("https://www.shmoocon.org/speakers_2013"):

> [I]"In forensics there is a new file system called ExFat. Microsoft has  made a deal with the SD Card Association to make ExFat the standard for  all SD cards over 32gigs. Microsoft has protected this property and is  doing everything it can to collect licensing fees for ExFat for any  device wanting to use the SD Associations standard. Many people do not  know are happening and the changes in cameras, which will eventually  affect every single new device from laptops, OSs, to tablets and phones.
[/I]
[I]
We have all been blindsided and Microsoft now owns the market for SD  larger than 32gigs and will BE PAID for every new device including Linux  based due to this change in storage media. In turn this  affects forensics, and adds additional costs to forensic equipment and  software. I will break down this new format and show how this cost is  implemented and educate people about SDXC, where it will be used."[/I]

Further, unless I'm mistaken, Linux can't be installed on ExFaT file systems, though Linux can now *mount* the file system. What this means, I gather, is that if one wants to install Linux on a MicroSD, it can't be done on any card larger than 32gigs, since every card comes with the following warning:
> 
"*Reformat into file system other than exFAT may cause instability...*"

So, does anyone know more about this latest issue? Educate me.

---

### Post by TheFu on 2014-01-16
FAT32 will work on larger SDHC, though it does have limits.  Friends use 64G FAT32 formated SDHC cards.
The ExFAT thing has been known for years. I think only Microsoft platforms limit FAT32 to 32G sizes and it wasn't always that way. There was an "upgrade" to the FAT32 file system on WinXP that put the limitations in. I can only guess it was a patent and marketing decision by Microsoft when they realized that larger portable storage would be needed in video and normal cameras. Their plan has worked ... though a few camera makers have put out a competing format. I doubt MS will include it until consumer demand reaches a point where they must.

That's all I know.  Read more about ExFAT history at wikipedia.


Oh ... Linux needs to be installed onto a Linux file system.  User, groups and permission bits are central to Linux security. I believe there is a Linux specific, flash memory write-kind file system. Don't know the name.

So, if you are looking to use larger SDHC/SDXC cards to load Linux like Unetbootin or Yumi support, just format those on Linux with FAT32.

---

### Post by neu5eeCh on 2014-01-16
Yeah, thanks. The Wikipedia doesn't really help me, though interesting. I didn't realize MS deliberately "sabotaged" FAT32 to "force" the use of the proprietary ExFat. You know, you can't blame a business for making money, but somehow MS always casts it in the worst of all possible lights.

Moving on.

I can't seem to find <32G MicroSD cards that are not limited to ExFat. Is there such a thing as an open format Micro SD?

---

### Post by TheFu on 2014-01-16
Google found a how-to on this. They used the standard tools **mkfs** and **parted** to do it. I suppose it would be easier to use **gparted**.
* delete any partitions on the card - make certain you are using the correct device - /dev/sdd or higher is probably correct. DO NOT LET the SDXC card be opened. If so, **umount** it. If you choose the wrong device (like any of your spinning HDDs), then the results will be catastrophic.
* create any partitions you want - vfat, ext[234], NTFS, whatever - use MSDOS/MBR partition table and tag the partition types as desired.
* make a file system and format it - vfat.
That should do it.

I don't have any SDXC storage, so cannot test.

---

### Post by Jonor on 2014-01-17
My 16Gb MicroSD intended as backup for a tablet won't format to ext4 with the Gnome Disk Utility, Gparted or command line but it took FAT32 okay.

---

### Post by neu5eeCh on 2014-01-17
Yeah, and that's part of the problem. FAT32 is *not* a good fit for Linux, though it will work.

The impression I'm getting is that makers of MicroSD cards have tailored the hardware of their cards to run on FAT or exFat systems (this is def. the case with MicroSDXC cards and hence the warnings of "instability" if exFat or FAT file systems aren't used). <Rant>This would also be in keeping with Microsoft's business practices. As with "winmodems", they're smart enough to create, in effect, Wincards. Why compete when you can create a Gatesian monopoly? Always, always, always with them, trying to lock out everybody else (UEFI Boot Loader). It's all about monopolizing and forcing markets rather than competing.</Rant>

Moving on. Again.

I'm beginning to think it's not possible to use <32 G  MicroSD cards unless Microsoft gets its cut. They're like little PCs, apparently, with their own little EUFIs that prevent anyone from using anything but Microsoft's licensed and fee'd product.

---

