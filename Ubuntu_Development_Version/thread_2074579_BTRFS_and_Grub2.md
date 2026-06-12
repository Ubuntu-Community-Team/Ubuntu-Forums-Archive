---
title: "BTRFS and Grub2"
date: 2012-10-21
forum: Ubuntu Development Version
---

### Post by Slug71 on 2012-10-21
Hope these two will play nice this time around.
I tried installing both 12.04 and 12.10 using BTRFS for both / and /home and Grub failed to install with each of them. Tried on both my Netbook as well as my test rig(P4). When I dig a little deeper, it seems Grub complains about core.img being "unusually large".....

An interesting observation I made today though. 
On my test rig I have a number of installations of numerous distros. Havent fired this up in a couple of years mind you so I still had the Lucid development install as the latest on here....lol.
On the box I had a install of Fedora 13(which was the latest stable at the time IIRC) on BTRFS. Installed as both / and /home. Fedora 13 still had legacy Grub and I remember Lucid with Grub2 not being able to boot Fedora 13.
Well last night I replaced the Lucid install with 12.04 on Ext4(since BTRFS wounldn't work) and then today decided to check if Fedora would boot. Sure enough it boots! :) So I KNOW they can play nice. 



It's good to be back. :popcorn:

---

### Post by oldfred on 2012-10-21
Is the issue that you are using gpt partitions without a bios_grub partition?

Grub has to have a place to install core.img. It normally with MBR installs in the sectors between the MBR and the first partition which now starts at sector 2048 or lots of room.  Some try installing to a PBR or partition boot sector, but then has to convert to blocklists or hard coded addresses.

---

### Post by ratcheer on 2012-10-23
I have Siduction Linux installed on gpt and btrfs. I could not get it to work until I found a tiny detail. As soon as I made the change, it has worked perfectly ever since. But, dern it, I thought I kept a log of everything I had to do to get the installation up. I cannot find a note on that.

It was something for which I used an advanced gdisk command to make a setting on the partition. I will try to find it and post back (and add to my installation notes, too).

Tim

---

### Post by ratcheer on 2012-10-23
Ah, I found it.

In gdisk, press "x" for advanced options, then press "a" for attributes. Then press the number of the partition you want to boot to, then press "2" to set the legacy boot flag.

I hope this helps you, too.

Tim

---

### Post by oldfred on 2012-10-23
Some more detail:

When we first started seeing gpt partitions the author of gdisk was sometimes in the forum. He said with gpt we should never set a boot flag on a gpt partition table, but then found some BIOS, particularly Intel motherboard need a boot flag to get anything to boot. Grub does not use boot flag, Windows has to have a boot flag on a primary partition in MBR. 

Add boot flag (even though not required with gpt) - see post by srs5694
[http://ubuntuforums.org/showthread.php?t=1563699](http://ubuntuforums.org/showthread.php?t=1563699)

Also the boot flag in gpt is used with UEFI systems to tell which partition is the efi partition. 
In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

Also is grub loading the btrfs.mod file like it does for ext?  
insmod ext2 

You need 
insmod btrfs

---

### Post by ratcheer on 2012-10-23
I don't know, but the first partition I created on my disk was the 2 MB EF02 "BIOS boot partition". Then I created the btrfs, then I installed Linux. I installed it several times, but could never get it to boot until I found out about and set that attribute.

Tim

---

### Post by Slug71 on 2012-11-01
> **oldfred said:**
> Is the issue that you are using gpt partitions without a bios_grub partition?

Grub has to have a place to install core.img. It normally with MBR installs in the sectors between the MBR and the first partition which now starts at sector 2048 or lots of room.  Some try installing to a PBR or partition boot sector, but then has to convert to blocklists or hard coded addresses.

Yeah thats the issue. Or at least I think. Seems my partitions are showing as msdos.

So are newer harddrives coming out with larger MBRs?

---

### Post by oldfred on 2012-11-01
MBR was fixed as a standard in the mid eighties when PC hard drives came out. 

The new standard is UEFI which has a full partition instead of the MBR and gpt partitioning. But with gpt you have to have the bios_grub partition as there is a whole different way of organizing the partitions. If you have a drive over 2TB you have to use gpt.

---

