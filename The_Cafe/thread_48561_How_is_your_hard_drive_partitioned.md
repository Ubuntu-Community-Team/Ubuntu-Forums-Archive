---
title: "How is your hard drive partitioned?"
date: 2005-07-13
forum: The Cafe
---

### Post by matthew on 2005-07-13
I thought this might be interesting. Here's my setup on my main computer.

Size: 80 Gb Hdd, currently dual booting Ubuntu with Win XP

Partitions:
Name/type/size/mountpoint

hda1    ntfs    15.3 Gb    WinXP  *mounts read-only as /media/windows in ubuntu
hda2    ext3   10 Gb       /
hda3    ext3   30.5 Gb    /home
hda4    extended, includes hda5 & hda6
  hda5    fat32    19.4 Gb    /home/matt/music  
  hda6    linux-swap    1 Gb  

hda5 and 6 used to be part of hda1's ntfs partition. As I am using XP less and less I decided to remove space from its partition and make a shared space accessible from both. Since I am now using XP for almost nothing, hda5 holds my mp3s and almost nothing else.

I didn't have a swap file to start out with because with 1 Gb ram I figured it wasn't necessary, but I created one now because I want to try to get the hibernate function to work. Haven't tried yet...soon, though.

EDIT on August 22, 2005: I had a hard drive failure today. More info on that [here.](http://ubuntuforums.org/showthread.php?p=314262#post314262)
  Anyway, here's my new partitioning scheme as I decided I don't need windows anymore:
1Gb linux-swap swap
30 Gb ext3 /
45 Gb ext3 /home

---

### Post by Athropos on 2005-07-13
Mine:
/ -> 30 GB (ReiserFS)
/boot -> 100 MB (EXT3)
/home -> 30 GB (ReiserFS)

+ other partitions I use for storage, mounted in /mnt and linked from my home directory.

---

### Post by dickohead on 2005-07-13
**On my desktop i have:**

*SuSE 9.2 / Windows XP Pro*

/dev/hda1 - NTFS - Win C:\ - 30GB
/dev/hda2 - NTFS - Win D:\ - 30GB
/dev/hda3 - Reiser - boot - 50mb
/dev/hda4 - SWAP - swap - 1GB
/dev/hda5 - Reiser - / - 28GB
/dev/hda6 - Reiser - /home - 30GB
/Music - SMB - network share
/Storage - SMB - network share
/home/tim/network - SMB - network share


**On my laptop:**

*Ubuntu Hoary 5.04 / Windows XP Pro*

/dev/hda1 - NTFS - C:\ - 30GB
/dev/hda2 - SWAP - swap - 1GB
/dev/hda3 - Reiser - / - 14GB
/dev/hda4 - Resiser -/home - 15GB
/Music - SMB - network share
/Storage - SMB - network share
/home/tim/network - SMB - network share


**And the server:**

*SuSE 8.2*

/dev/hda1 - SWAP - swap - 1GB
/dev/hda2 - Resier - / - 79GB
/dev/hdb3 - Ext3 - /home - 20GB

---

### Post by Lowe on 2005-07-13
/dev/discs/disc0/part5 swap 3GB
/dev/discs/disc0/part1 / ext3 10GB
/dev/discs/disc0/part6 /home ext3 180Gb

---

### Post by sapo on 2005-07-13
/ = 20GB - ReiserFS
/home = 10GB - ReiserFS
/mnt/media = 45GB - ReiserFS

 :grin:

---

### Post by qalimas on 2005-07-13
All on one harddrive, all etx3:

/ - 27.5gb (i had the space, so why not? ;))
swap - 1gb
/music - 9.2gb (obviously...)
/iso - 31.2gb (used to store linux iso files ;))
/files - 45.8gb (used for storage of... just about everything from downloads to my current projects)
/vmware - 30.5gb (no longer used -- yay :D, I just haven't found a use for this empty place yet)

---

### Post by Curlydave on 2005-07-13
80GB SATA drive: WinXP Pro

40GB ATA drive: Ubuntu 5.04

---

### Post by sonny on 2005-07-13
Mine:

Master: 200 gb (Not quite, but don't remember the exact numbers)

hda1 ext3 36gb /
hda2 SWAP 1 gb
hda4 ext3 163 gb /home

Slave: 20 gb (lap top HD)

hdc1 ext3 20 gb /usr

---

### Post by Kyral on 2005-07-13
Ubuntu Hoary 5.04

300 GB IDE

20 GB / ext3
1.5 GB Swap
rest /home ext3

160 GB SATA FAT32 (easier to set permissions in the fstab :D) mounted on /media/anime and individual anime dirs symlinked into /home/anime

---

### Post by super on 2005-07-13
hda1 ntfs    5gb     /WinDoze
hda2 fat32  50gb   /Multimedia
hdb1 ext3   20gb    /
hdb2 swap  600mb
hdb3 ext3   20gb   /home/david

works for me! i am thinking of switching to reiserfs tho.

---

### Post by jerome bettis on 2005-07-13
hda1  extended - 34 gb
hda2  /windows - 6 gb fat 32
hda5  /boot - 25 mb ext2
hda6  / - 400 mb reiser4
hda7  /usr - 6 gb reiser4
hda8  /var - 2.5 gb reiser4
hda9  /home - 21 gb reiser4
hda10 swap 1024 mb

---

### Post by XDevHald on 2005-07-13
Windows XP Pro: 37GB
Ubuntu Hoary 5.04: 38GB // **Swap: **1.5GB

---

