---
title: "using Live CD look for stuff in XP- help needed.."
date: 2008-08-21
forum: Windows
---

### Post by scotcella on 2008-08-21
Okay, my sister has a HP Pav Desktop PC, my understanding from minimal information grasped by a very computer illiterate darling, it has XP. It is suffering from the blue screen of death. 

I want to try and recover the PC with the XP OS if I can but I am allowed to install Ubuntu if I want to..  personally I'd be slapping on ubuntu on it, but it's a computer illterate's PC and I would like to recover and format the drive with XP if I can for familiarity's sake......

If I remember right HP started selling these PCs with a recovery disk internally rather selling them with CD disks so I am hoping that I can do this..   but....
[B]
First Issue:[/B]
I cannot boot up the internal recovery XP thingy to reformat the pc by pressing F10 continously,  it keeps showing a black screen. 

But it boots the Live CD  pressing F10 continuously and boots the CD drive just fine... or maybe it doesn't have an internal recovery thing, 

How do i find out if it has the internal XP CD recovery thing?

(She's lost all documentation and manuals for the computer..  grr)

If I go to the BIOS set up blue screen- has information about the PC but there is no information anywhere about using the internal recovery thing. Only BIOS information, which boot order and so on.

**Second Issue:**

Before I do anything I would like to recover any data that I can find. My sister in law says that she has taken them off the computer, and I'm not sure what she means by that. Rememeber she's computer illiterate!

I know the computer has 250GB HDD..  the fdisk output shows this.....

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       29321       30401     8683132+   c  W95 FAT32 (LBA)



```

Using Places -> My computer, then picking the harddrive it only shows as 8.9GB. I can open it but there is nothing there..  zilch. I believe that this is probably the "recovery" disk thing, but there is nothing inside. Where are the remaining GBs...?

ARGH..  I don't know what to do next..  any pointers to get me going would be really appreciate thanks!!

Specs that I found on the side of the computer... not sure if this will help but...

Intel Pentium D Prcessor
1024MB DDR2 SDRam Mem
200GB ATA HDD
Nvidia Geforce 7500OLE

OS: XP Media Centre...

---

### Post by MaxIBoy on 2008-08-22
"Recovery thing" would be a partition. It probably wouldn't act like a recovery CD, it would contain recovery data which is only readable from within Windows. I know this because my PC started its life as a Compaq prefab, and Compaq is owned by HP. I eventually just used the recovery partition to install Ubuntu in.


I would start up something like Gparted, look at the partition map, see which /dev/sda-whatever is bigger, and mount that one.

Does this computer have multiple optical drives, (so you can use one for a bootCD and the other one to burn some backup disks?) If not, try backing up to an external HDD, or even getting an external HDD enclosure and putting her 250 GB HDD into it. 

I've had an XP system which was borked almost as bad (XP itself wasn't borked, my MBR was.) I had a techie friend install XP on the same partition without overwriting my stuff, then configured GRUB to use that installation. I wouldn't be able to do the same, I wouldn't know how to edit GRUB for Windows. All I'd be able to do is move all the files somewhere else, and reformat/reinstall. 

Another thing I did as a temporary fix was get an old HDD and stick it in the machine, install XP on that, and leave the main HDD in too. The thing is, the one I got failed in about a week (someone had had it lying around for years and gave it to me for free.)

---

### Post by Sef on 2008-08-22
To grab the data you want to save download [Knoppix]("http://knoppix.com").  It functions great as a resuce cd.

---

