---
title: "How do you have your partitions setup"
date: 2007-01-19
forum: The Cafe
---

### Post by kd7swh on 2007-01-19
I am just wondering how everyone likes their partitions. How many of you dual boot? Do you have a separate partition for your /home?

---

### Post by enopepsoo on 2007-01-19
I have a 20 gig for Ubuntu, 10 gigs that aren't in use and a 130 gb /home, as well as as 120 gb and 250 gb partitions
:guitar:

---

### Post by bigken on 2007-01-19
80 gig hdd

25 gig winxp

10 gig /system

2gig /swap

wots left /home ;)

---

### Post by public_void on 2007-01-19
```

Device Boot      Start         End      Blocks    Id   System
/dev/hda1               1          784   6297448+ 1b   Hidden W95 FAT32 (6GB OEM added for system restore) 
/dev/hda2   *       785        5234   5744625     7   HPFS/NTFS (34GB Windows)
/dev/hda3          5235       6016   6281415    83  Linux (6GB Ubuntu)
/dev/hda4          6017       6081     522112+  82  Linux swap / Solaris (512MB Swap)
```

I like to have one big partition, rather than separate partitions for /home or /boot etc.

---

### Post by ~LoKe on 2007-01-19
> Disk /dev/sda: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2325    18675531   83  Linux
/dev/sda2            2326        2431      851445    5  Extended
/dev/sda5            2326        2431      851413+  82  Linux swap / Solaris

Home:
> Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
Debating on whether or not to take this 20GB drive out and just put it all on the same drive.  This IDE beast is loud.

---

### Post by meng on 2007-01-19
Spelling Nazi alert!
I like to have a **separate** /home partition.

---

### Post by Omnios on 2007-01-19
Hi hi I have a bit of a weird set up. First I tri boot with a Ubuntu partition a Fedora partition and a XP partition. I also have a fat32 documents partition that I have set up as a XP document drive and also mounted in Linux as a document drive that works really well with update installs etc and dont have to worry about weeding out a new home partition. As for XP I bearly ever use it so now its mostly for Ubuntu documents.

---

### Post by kd7swh on 2007-01-19
> **meng said:**
> Spelling Nazi alert!
I like to have a **separate** /home partition.

My life is a typo.

> How do you have your **partions** setup

---

### Post by sloggerkhan on 2007-01-19
hey, spelling Nazi:
Seperate hom partishin, 2 Oobuntoo partishins (Won fore w/beril, won fore W/O it, pluz mor patitions and unpartishind space... fer duh fyootoor.)
;)

---

### Post by po0f on 2007-01-19
```
[FONT="Courier New"]hda (120G)
  hda1 /boot  128M
  hda2 swap   2G
  hda3 extended
  hda5 /      25G
  hda6 /home  80G  # Gonna shrink this down, I just got a 160G external
  hda7 /usr/local  10G
  hda8 /tmp   256M

hdb (80G)
  empty, waiting for F7 (Fedora 7, they dropped the "Core")

sda (160G)
  sda1 /media/storage 120G[/FONT]
```

Since I have a fairly big external hard drive, and pending F7's release, I'm going to move a lot of stuff around.  Oh yeah, I never, ever use all the space on a hard drive.  You never know when you need one more partition.  :)

---

### Post by slimdog360 on 2007-01-19
Two hard drives with the first separated into 3 partitions, /root, /home, and swap. The second hard drive is split in two with a special /admin and /music partitions within my /home partition.
The /admin is for my wallpapers, themes, stuff like that.

---

### Post by DJ_Peng on 2007-01-20
I must be the total odd ball. I got an old(-er) WinXP box when someone upgraded theirs, and my old box was already set up with a drive set up for Ubuntu and a separate drive for my files. When I got this box I ended up migrating both my old drives into it and now have a three-drive system.
```
hda1       20.09 GB       NTFS         WinXP (because I still use it for my radio work and some
                                                 Dreamweaver/Fireworks work, although I also have them installed under Wine)
hda2                                           W95 Extended Partition (LBA)
hda3       13.98 GB       ext3          Ubuntu Edgy (including /home)
hda4       67.72 MB       FAT16       Originally set up for PartionMagic's boot util, now no longer used
hda5      352.96 MB                      Linux swap
hda6       40.04  GB      FAT32       Primary data storage, including Firefox and Thunderbird profiles

hdb1       18.66 GB       ext3          Older Ubuntu Edgy install, kept to retain some old data
hdb2                                          W95 Extended Partition (LBA)
hdb5      352.86 MB                     Linux swap

hdc is my CD-ROM drive

hdd1       14.32 GB       FAT32       UbuntuData, data files that are primarily used for Ubuntu, but also available to
                                                 WinXP, including some install downloaded files
```
Eventually I'll reformat hdb and move the files from hdd to it, and if I can ever get SAM Broadcaster to work within Wine I'll gladly blow away my Windows partition and give Ubuntu that space.

---

### Post by K.Mandla on 2007-01-20
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          12       96358+  83  Linux      /boot
/dev/hda2              13         510     4000185   83  Linux      /
/dev/hda3             511         572      498015    5  Extended
/dev/hda4             573        7296    54010530   83  Linux      /home
/dev/hda5             511         572      497983+  82  Linux swap / Solaris
```
I occasionally mess with strange file systems, so I've gotten into the habit of a separate /home and /boot, so I can keep Grub happy (if I remember right, it only wants ext2 or 3 ... or maybe some others :roll: ).

---

### Post by kevinf311 on 2007-01-20
My first partition is like an 80GB XP section which I wish was the second partition every day of my life. The second partition is a 40GB Ubuntu 6.06 partition that is about half full and only growing. I might get rid of my Zip Drive and add another hard drive to migrate storage to, keeping only the OSes on the first drive.

---

### Post by KaeseEs on 2007-01-20
100 MB /boot
21.5 GB /
241 GB /home
1 GB swap
~50 GB free, so I can copy my 'doze partition from my other machine

---

### Post by bionnaki on 2007-01-20
how do you setup a /home partition without reformatting?

---

### Post by Malta paul on 2007-01-20
Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4776    38363188+  83  Linux
/dev/hda2            4777        4982     1654695    5  Extended
/dev/hda5            4777        4982     1654663+  82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       12306    78365070    5  Extended
/dev/sda3           12307       14593    18370327+   7  HPFS/NTFS
/dev/sda5            2551        8287    46082421    7  HPFS/NTFS
/dev/sda6            8288       12306    32282586    7  HPFS/NTFS

That,s it :)

---

### Post by dorcssa on 2007-01-20
I have 5 gig for /, 4 gig for /home, and three other partitions, two 37 gig and one about 63 gig. I don't dual boot since december. :)

---

### Post by EdThaSlayer on 2007-01-20
I have one huge partition that includes Ubuntu and my /home file. The second and third partitions are from my extra hard drives inside my pc.

---

### Post by shining on 2007-01-20
fdisk -l 
> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/sda2            1217        6079    39062047+  83  Linux
/dev/sda3            6080        7538    11719417+   5  Extended
/dev/sda4            8721        9729     8104320    c  W95 FAT32 (LBA)
/dev/sda5            6080        6322     1951866   82  Linux swap / Solaris
/dev/sda6            6323        7538     9767488+  83  Linux


df -h
> 
Sys. de fich.         Tail. Occ. Disp. %Occ. Monté sur
/dev/sda6             9,2G  7,2G  1,6G  82% /
/dev/sda2              37G   26G  9,7G  73% /data


sda1 : windows originally installed, unused
sda2 : data partition, mounted in /data
sda4 : hp windows recover partition crap
sda6 : / partition for debian

and I've some free space left (~10 GB, 7539-8720) potentially for a second linux distribution, which could then also use the swap and data partition.

---

### Post by happy-and-lost on 2007-01-20
(55GB HDD)
1. Extended partition containing a 5GB Ext3 partition for Ubuntu and a 5GB partition for whatever other distro I'm playing around with (Debian currently)
2. Primary NTFS 10GB (eew) for WinXP. I was not going to let it be first this time :p
3. 30-something GB /home in Ext3
4. 1GB Swap

---

