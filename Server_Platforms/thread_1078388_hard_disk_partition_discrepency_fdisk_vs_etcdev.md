---
title: "hard disk partition discrepency: fdisk vs /etc/dev"
date: 2009-02-23
forum: Server Platforms
---

### Post by Eddy Gordo from Tekken on 2009-02-23
Ubuntu Server 8.10
Mobo/CPU: Asus M37A78-EM / AMD Sempron 64 3800+
Ram: 1GB
system drive: Hitachi deskstar 250 GB, 7200 rpm
Raid: Highpoint Rocketraid 3520
Storage Drives: 4 X WD Cavior 1TB (Raid 5)

In my system, the RAID array is sda, the OS is installed on sdb.

fdisk results...
```
:~$ sudo fdisk -l

disk /dev/sda: 3000.3 GB, 30000370200576 bytes
255 heads, 63 sectors/track, 386774 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

    Device Boot   Start    End       Blocks        Id   System
/dev/sda1             1   267350     2147483647+   ee   GPT

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

    Device Boot   Start    End       Blocks        Id   System
/dev/sdb1    *        1   30122     241954933+     83   Linux
/dev/sdb2          30123  30401       2241067+     5    Extended
/dev/sdb5          30123  30401       2241036      82   Linux swap /Solaris
```

```
ls /dev results...
:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sdb  /dev/sdb1  /sdb2  /dev/sdb5
```

I want the raid array, sda, to be one contiuous partition. Why does fdisk show one partition, but the /dev directory shows two partitions?

Also, I used fdisk to format sda in ext3.  In fstab, the drive shows ext 3.  But In the fdisk -l results, why does it say GPT instead of ext3?  

fstab... 
```
#  /etc/fstab: static file system information.
#
#  <file system>  <mount point>   <type>  <Option>    <dump>   <pass>
proc               /proc           proc    defaults    0       0
#  /dev/sda1
UUID=4ed3b515-f037-422e-8103-89672ea44acd /      ext3   realatime,errors=remount-ro  0   1
#  /dev/sda5
UUID=3de70bf2-deb2-4ec7-bd1b-214fd9ad9688  none        swap   sw  0     0
/dev/scd0        /media/cdrom0 udf,iso9660  user,noauto,exec,utf8  0    0
```

---

### Post by fjgaude on 2009-02-23
GPT is the partition table type, not the filesystem class. GPT is for huge drives, beyond default. This is a good thing.

Can't say why you have an sda2 partition. How was the raid5 created and by whom?

---

### Post by Eddy Gordo from Tekken on 2009-02-23
Thanks.  Explaining ‘GPT’ prompted me to get acquainted with that.  Using GNU Parted results this….

```
:~$ parted /dev/sda

(parted) print
Model: HPT DISSK 0_0 (scsi) 
Disk /dev/sda: 3000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number	Start		End		Size		File system	Name	Flags
1		17.4kB		2998GB	2998GB	ext3
2		2998GB	3000GB	2298MB	linux-swap
```

I believe I know what happened.  Long story short, I was having probs loading the OS in this box, and part of my troubleshooting included trying to install it on the raid array to see if it worked.  It did not.  I did get it to finally work on the current drive.  The linux-swap partition must be residue left over from that install.  So that, I think, solves the mystery of sda2 appearing in the /dev directory.  However, why doesn’t it show up in fdisk?

Also, what is the best method of creating one continuous file system on sda?  My newb intuition tells me to use gnu parted to delete the unwanted partition, sda2.  Then extend the first partition to the end of the drive…

```
:~ parted /dev/sda
(parted) rm 2
(parted) resize 1 17.4kB 3000GB
(quit)
```

According to the gnu parted manual, I can’t change the ‘start’ of ext3 file system.  Its only 17k, but it’s MY 17k.  Also, gnu parted doesn’t create ext3 file system. So to salvage that 17k, I’d have to delete both partitions, and then create a new one.  Then write a new file system, right?

So is this better…
```
:~ $parted /dev/sda
(parted) rm 2
(parted) rm 1
(parted) mkpart 0 -0
(parted) quit

:~$  mkfs.ext3 /dev/sda1
```

I don’t really understand all the options involved with mkfs.  I found this command in a how to for creating ext3 file systems (I can’t remember where).  Will this suffice or are the options necessary / useful?


> How was the raid5 created and by whom?
I created the raid 5 array using the raid controller's bios.  When i boot the computer, the controller bios loads before the mobo bios, allowing me to (re)build and maintain raid arrays attached to the controller.  There are four physical drives attached, 1TB each.

---

### Post by fjgaude on 2009-02-23
> I&#8217;d have to delete both partitions, and then create a new one. Then write a new file system, right?

So is this better&#8230;
Code:

:~ $parted /dev/sda
(parted) rm 2
(parted) rm 1
(parted) mkpart 0 -0
(parted) quit

:~$  mkfs.ext3 /dev/sda1

I don&#8217;t really understand all the options involved with mkfs. I found this command in a how to for creating ext3 file systems (I can&#8217;t remember where). Will this suffice or are the options necessary / useful?

Looks right to me... do these things and you are good to go with an ext3 filesystem on one large, single partition.

Thanks... and good luck with the raid card. What do you do when the card fails? Buy another? Make backups of all important data. I use triple backups.

---

### Post by Eddy Gordo from Tekken on 2009-02-23
> and good luck with the raid card

wow, that sounds ominous.  do you know something that I don't? I do intend to have a backup drive for important stuff.  If the card fails, I supposed I'd be screwed.  is it possible to salvage an array created on a different raid controller?  I plan on building a new gaming rig soonish.  when that is up, I'll some of my old parts on my lan in some fashion, perhaps a 2nd back up...until then i'll make due with what i have, which is one big array, and a smaller 1TB to back up important things.

thanks again for the help.  once I understood my question I was able to read-up the answer I needed.

---

### Post by fjgaude on 2009-02-23
Well, raid cards are such that no two have the same format for what they do. So to protect the array only the same model one can be used if one fails.

Arrays are no excuse for not doing backups. Sooner or later you will have a hardware failure in which a raid5 array is corrupted and it will not re-build.

That's the short of the story.

---

