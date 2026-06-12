---
title: "OSS Disk Cloning solution for a non-profit"
date: 2008-08-31
forum: The Cafe
---

### Post by Pontifex_Maximus on 2008-08-31
I'm searching for an OSS solution that:

1) LiveCD based or PXE bootable
2) Can burn a disk image to a local hard drive, via pulling a disk image from a central server
3) Can do it on diverse hardware
4) Can work with minimal user intervention
5) Has a friendly and intuitive interface

Bonus points:

* Multicast support
* Auto-size partitions to fill any sized disk

Other considerations:

* Preference for free software
* Low cost or small cost to non-profits are okay


Long winded explanation:

I'm doing some work for a local non-profit (Computers for Classrooms).  They do *a lot* of volume:  Testing computers for functionality, installing Operating Systems (Ubuntu and Windows) and installing other programs (AV, Anti-Adware, Teaching Tools, other free programs, etc).  This takes quite a bit of time, as you can imagine.

Being the enterprising volunteer that I am, I wanted to find them software to automate the task of getting software onto their computers.  This seems to be best handled by Windows Deployment Services, on the Microsoft side.  And Clonezilla on the OSS side.  WDS fulfills all my requirements, but is Microsoft.

For OSS the potential is there.  Heck, Knoppix + DD + SMB + Parted would do the job in a basic fashion; Some automation with Python / Perl could round it out.  But am I to assume that no one has put together anything as of yet?

---

### Post by Polygon on 2008-09-01
partimage is the program your looking for. can create exact clones of hard drives of many filesystems (including ntfs), and is in the reops. you can just create your own ubuntu livecd with that program installed, or find some other livecd with it included.

---

### Post by mips on 2008-09-01
[COLOR=Red]**Clonezilla**[/COLOR], [http://www.clonezilla.org/](http://www.clonezilla.org/)

> 
**[COLOR=#3333ff]Features of Clonezilla[/COLOR]**

 
[LIST]
[*]Free (GPL) Software.
[*]Filesystem supported: ext2, ext3, reiserfs, xfs, jfs of GNU/Linux, and FAT, NTFS of MS Windows. Therefore you can clone GNU/Linux or MS windows. For these file systems, only used blocks in partition are saved and restored. For unsupported file system, sector-to-sector copy is done by dd in Clonezilla.
[*]LVM2 (LVM version 1 is not) under GNU/Linux is supported.
[*]Multicast is supported in Clonezilla server edition, which is suitable for massively clone. You can also remotely use it to save or restore a bunch of computers if PXE and Wake-on-LAN are supported in your clients.
[*]Based on [ Partimage]("http://www.partimage.org/"), [ntfsclone]("http://www.linux-ntfs.org/") and dd to clone partition. However, clonezilla, containing some other programs, can save and restore not only partitions, but also a whole disk.
[*]By using another free software [drbl-winroll]("http://drbl-winroll.sourceforge.net/"), which is also developed by us, the hostname, group, and SID of cloned MS windows machine can be automatically changed.
[/LIST]
I think the above meets all your requirements as specified. Have a look at the site and read the testimonials.

---

