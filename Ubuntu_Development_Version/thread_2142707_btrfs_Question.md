---
title: "btrfs Question"
date: 2013-05-06
forum: Ubuntu Development Version
---

### Post by roly33 on 2013-05-06
Does btrfs use Disk Compression or has the About This Computer gone a bit screwed up in the 13.10 Development Release, as About This Computer is saying that my 250GB HDD is a 500.1GB HDD?

[ATTACH=CONFIG]242262[/ATTACH]

Roland

---

### Post by Cheesemill on 2013-05-06
Btrfs does have the ability to use compression, but it isn't enabled by default. I doubt you would get that level of compression out of it anyway.
What's the output of....
```
sudo parted -l
```

---

### Post by roly33 on 2013-05-06
> **Cheesemill said:**
> Btrfs does have the ability to use compression, but it isn't enabled by default. I doubt you would get that level of compression out of it anyway.
What's the output of....
```
sudo parted -l
```

This is the output of sudo parted -l


roland@steelers:~$ sudo parted -l
[sudo] password for roland: 
Model: ATA Hitachi HTS54502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  btrfs        boot


roland@steelers:~$ 

Roland

---

### Post by grahammechanical on 2013-05-06
As regards my system. I would say that Details should be recording the size (approximately) of the partition it is installed upon and not the whole hard disk. In my case I have Saucy in 21GB ( / ) and 27GB (/home) and Details is showing 47.3GB. That is why I say approximately. Ext4, by the way.

Regards

---

### Post by Cheesemill on 2013-05-06
I'm getting the same behaviour as always on my machine, the total size of all installed drives...

[ATTACH=CONFIG]242272[/ATTACH]

I'm using LVM + ext4 on my drives so it looks like this is only an issue with btrfs. Do you just have a simple btrfs setup or are you using any of the advanced features? I can imagine that creating a snapshot of a 250GB partition may cause the issue you are seeing if it appears as two seperate 250GB drives to the system.

---

### Post by Rukiri on 2013-05-07
> **roly33 said:**
> Does btrfs use Disk Compression or has the About This Computer gone a bit screwed up in the 13.10 Development Release, as About This Computer is saying that my 250GB HDD is a 500.1GB HDD?

[ATTACH=CONFIG]242262[/ATTACH]

Roland

Okay, did you at any point do btrfs device add /xxx/xxxx / ?  
I've used btrfs for quite awhile and I've never seen this much compression, also I would refrain from using lvm (it's slow... at R/W even on my SSDs)

---

### Post by jerrylamos on 2013-05-07
I don't know anything about btrfs (!).  On a mulit-partition setup with Pangolin, Windows 7, etc. I tried specifying btrfs on a saucy install and promptly got a couple abends.  One message indicated a problem with another partition not even the one I was installing to.

Ext4 worked fine.

---

### Post by roly33 on 2013-05-07
> **Cheesemill said:**
> I'm getting the same behaviour as always on my machine, the total size of all installed drives...

[ATTACH=CONFIG]242272[/ATTACH]

I'm using LVM + ext4 on my drives so it looks like this is only an issue with btrfs. Do you just have a simple btrfs setup or are you using any of the advanced features? I can imagine that creating a snapshot of a 250GB partition may cause the issue you are seeing if it appears as two seperate 250GB drives to the system.

I've just got 1 Partition / with no /swap or /home partitions.

> **Rukiri said:**
> Okay, did you at any point do btrfs device add /xxx/xxxx / ?  
I've used btrfs for quite awhile and I've never seen this much compression, also I would refrain from using lvm (it's slow... at R/W even on my SSDs)

 I just created the single btrfs partition using the Something Else option in the Installer, my Daily Build Disk wouldn't let me Install properly through just the Installer so I had to Install from the Live Session, if that could have caused this?

I'm not to bothered as it's not effecting anything, unless Toshiba have used a 500GB HDD and limited it to 250GB and only btrfs sees the rest (not even sure that's possible with SATA, but I know PATA HDDs can be limited through Jumper settings).

Roland

---

### Post by IanW on 2013-05-07
ISTR Grub may have issues if /boot is on a btrfs partition.

> **Ubuntu Documentation]

As of 11.04, it is possible to use only btrfs file systems with the caveat that grub 'MUST NOT' be installed to the boot sector of the btrfs volume containing /boot.
See also Ubuntu Grub2 Bug 757446 and Ubuntu Grub2 Bug 759772. You must install it to either the parent (sda rather than sda1 said:**
>  forum post[/URL].

When installing Ubuntu in one large btrfs-Partition without an extra boot-partition, take care to keep about 1 Mib space free at the beginning of the disk.
This is possible using the partition manager in the Ubuntu installer. When there is not this space, the installer fails at the end when trying to install Grub! 

[https://help.ubuntu.com/community/btrfs]("https://help.ubuntu.com/community/btrfs")

---

### Post by roly33 on 2013-05-08
> **IanW said:**
> ISTR Grub may have issues if /boot is on a btrfs partition.



[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

Strange as I'm not having any problems with Grub, just HDD gaining an extra 250.1GB.

What are the best Partition Sizes e.g size of /boot, /swap, /home & / for a 250GB HDD with 3.7GB of System RAM (using the Ubuntu Installer numbers as I can never work out the MB & GB sizes with the long number format that the Installer uses)?

Roland

---

