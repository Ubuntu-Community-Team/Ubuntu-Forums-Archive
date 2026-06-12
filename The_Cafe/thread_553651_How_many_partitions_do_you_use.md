---
title: "How many partitions do you use?"
date: 2007-09-18
forum: The Cafe
---

### Post by curiousnoob on 2007-09-18
I saw this webpage ( [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) ) and was thinking the best option seemed to be the 4th option down.  The one with 5 partitions.  
My question is what size should the various partitions be and can this all be done with the live cd?

---

### Post by meborc on 2007-09-18
i use 4 partitions.. 1 for xp.. 1 for music, video etc (accessible by both xp and linux).. 1 ext3 partition for linux.. 1 swap partition

i don't use separate /home partition as i have all my doc's and media on the media partition and i like to start from a clean sheet every time i reinstall linux on ext3

---

### Post by alienexplorers on 2007-09-18
I use 4 partitions.  hdb1=/ (10GB), hdb2=/home (10GB), hdb3=/graphics (9GB), hdb6=Data backups (4GB), hdb5=swap

> Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1284    10313698+  83  Linux
/dev/hdb2            1285        2566    10297665   83  Linux
/dev/hdb3            2567        3716     9237375   83  Linux
/dev/hdb4            3717        4865     9229342+   5  Extended
/dev/hdb5            4291        4865     4618687+  82  Linux swap / Solaris
/dev/hdb6            3717        4290     4610592   83  Linux


---

### Post by jombeewoof on 2007-09-18
I use 4 across my 2 disks.
/hda1 /windowsxp
/hdb1 /
hdb2 /data
/hdb3 swap

on my laptop I don't dual boot, so I just have / and /data

---

### Post by forestpixie on 2007-09-18
I've got 6 across 2 disks

root, home, swap, docs, music and 1 that's got gutsy on at the moment

the main thing is to either have a /home or do as meborc does - makes reinstallation easy.

---

### Post by Sef on 2007-09-18
Moved to Community Cafe.  

As for me: 3 - root, home, and swap.

---

### Post by misfitpierce on 2007-09-18
2 - Ubuntu and swap... No seperate home drive.

---

### Post by reacocard on 2007-09-18
I use 6

/
/boot
/home
/var
/usr
swap

all ext3 except /boot which is ext2 (and swap which is swap). You really don't need this many though, just having swap, / and /home is plenty for most people.

---

### Post by Bachstelze on 2007-09-18
```
firas@Ana ~ $ mount
/dev/hda7 on / type ext3 (rw,noatime)
/dev/hda8 on /tmp type ext3 (rw,nosuid,nodev,noatime)
/dev/hda9 on /usr type ext3 (rw,nodev,noatime)
/dev/hda10 on /var type ext3 (rw,nosuid,nodev,noatime)
/dev/hda1 on /boot type ext3 (rw,nosuid,nodev,noatime)
/dev/hda6 on /data type ext3 (rw,nosuid,nodev,noatime)
/dev/hda2 on /ubuntu type ext3 (rw,nosuid,nodev,noatime)
/dev/hda11 on /slack type xfs (rw,nosuid,nodev,noatime)
/dev/hda12 on /openbsd type ufs (ro,ufstype=44bsd)
/dev/hda14 on /openbsd/tmp type ufs (ro,ufstype=44bsd)
/dev/hda15 on /openbsd/var type ufs (ro,ufstype=44bsd)
/dev/hda16 on /openbsd/usr type ufs (ro,ufstype=44bsd)

```

enough ? :p

---

### Post by PartisanEntity on 2007-09-18
I use 3, one for xp, one for ubuntu and one in fat32 that's shared between the two.

---

### Post by newman on 2007-09-18
hda1 /
hda2 /swap
hda3 /home

---

### Post by dptxp on 2007-09-18
10 GB XP - FAT32
10 GB / EXT3
10 GB ext3 for data and/or for trying other OS.
15 GB FAT32  Data to be able able to read/write from XP and Linux. I do
not want XP to read/write any ext3 partitions as it can damage them.
13 GB /home  EXT3
2 GB SWAP. So that I do not run of memory easily on 512 MB RAM machine.

This is on 60 GB HDD (Laptop).

A bit different on 80 GB HDD on Desktop.

---

### Post by RageOfOrder on 2007-09-18
A few :P

/dev/sda - Linux hard drive - 80GB
sda1 /boot
sda2 /swap
sda3 /
sda4 /home

/dev/sdb - Windows hard drive - 200GB
sdb1 - equivalent of /
sdb5 - Windows folder (equivalent of /boot)
sdb6 - Storage (equivalent of /home)

/dev/sdc - Music hard drive - 320GB
sdc1 - music
sdc2 - backup

How's that?


My laptop has one 160GB hard drive with four partitions
1 for /boot
1 for Slackware's /
1 for Sabayon's /
1 for /home

---

### Post by zekica on 2007-09-18
I have four partitions on both my desktop and laptop:
hda: (80GB)
hda1 - 10GB - / for feisty (ext3)
hda2 - 5GB - for testing, currently / for gutsy (ext3)
hda5 - 63GB - for data (music, movies, photos, documents etc) (ext3)
hda6 - 1GB - swap

Laptop:
sda: (40GB)
sda1 - 7GB - / for feisty (ext3)
sda2 - 5GB - for testing, currently / for OSX 10.4.10 (hfsplus)
sda5 - 25GB - for data (ext3)
sda6 - 1GB - swap

---

### Post by Ultra Magnus on 2007-09-18
Due to being careless when installing I have 6 partitions

1 - Dell Utility - Forgot to delete
2 - Vista Partition - Probably Will Delete
3 - 6 Mb of free space (Have no idea why- but too lazy to fix)
4 - /
5 - /home
6 - /swap

---

### Post by samjh on 2007-09-18
sda1 = /
sda2 = /home
sda3 = swap

---

### Post by AndyCooll on 2007-09-18
Traditionally I've usually just left Ubuntu to do a default install, so that would mean a root partition and a swap partition. And then I've added an extra drive to my file-server which is where I keep all my stuff.

Recently however, I've started putting the /home on a separate partition.

:cool:

---

### Post by tom-ubuntu on 2007-09-18
sda1 /boot  ext3
sda2 swap swap
sda3 / xfs
sda4 /home xfs

---

### Post by Gargamella on 2007-09-18
> **meborc said:**
> i use 4 partitions.. 1 for xp.. 1 for music, video etc (accessible by both xp and linux).. 1 ext3 partition for linux.. 1 swap partition

i don't use separate /home partition as i have all my doc's and media on the media partition and i like to start from a clean sheet every time i reinstall linux on ext3

the same for me.:)

---

### Post by justinin3d on 2007-09-18
200GB for XP

Ubuntu 7.04
10GB for ext3 /
1GB for swap
39GB for ext3 /home

basically the same has the ubuntu screencasts!, which are awesome, too bad ubuntu (or linux in general) has trouble with ntfs, hopefully this is fix on future releases, 

cant wait for 7.10 release next month!

---

### Post by Iceni on 2007-09-18
Let's see:
There are 6 disks in this computer, a total of 11 partitons - 3 for linux and two disks splitted in half. 

250gb xp disk, one partition
320gb ubuntu disk, three partitions
250gb media disk, two partitions
250gb media disk, two partitions. 
200 gb disk, right now empty.
160 gb disk also empty. Usually I use these two for testing distros etc.

---

### Post by public_void on 2007-09-18
I have 3 partitions:
ext3 - Root
swap - Swap
NTFS - Windows XP

I don't need any more, i.e. for home.

---

### Post by pain of salvation on 2007-09-18
1 for XP
/
/home
/var
another for music and videos mounted in /home/alvaro/Arquivos

---

### Post by mivo on 2007-09-18
Just three in this machine. 10 GB for /, 235 GB for /home, and 1 GB for swap. There's an external 80 GB disk that I use for backup purposes, but it is not always connected.

---

### Post by aninaiian on 2007-09-18
I currently have four on my 40 GB hardrive

5GB /
1GB swap
7GB /home
and the rest is used as a place to store my media files.

Thinking of changing the scheme as kernel compiling sometimes of fills up /.  However, I rarely use more than 2GB mark for /.

---

### Post by Scruffynerf on 2007-09-19
5 partitions across 2 drives.

Drive 1:
NTFS (XP)
EXT3 (Ubuntu)
Swap (Ubuntu)

Drive 2
NTFS (XP Storage)
Ext3 (Ubuntu Storage)

---

### Post by Shazaam on 2007-09-19
Real or virtual?

Physical=
Disk /dev/hda: 80.0 GB, 80026361856 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS  (WinXP)

Disk /dev/sda: 320.0 GB, 320072933376 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    5  Extended
/dev/sda5               1         781     6273319  82  Linux swap
/dev/sda6             782        3350    20635461   83  Linux   (PuppyLinux)
/dev/sda7            3351        8471    41134401   83  Linux   (Mepis)
/dev/sda8   *        8472       38849   244011253  83  Linux  (Ubuntu)

Virtual on Ubuntu host=
hda
1. /swap
2. DSL
3. PuppyLinux
4. Knoppix
5. Mepis

hdb
1. /swap
2,3, & 4 Mandriva /boot /root & /home
5. Ubuntu

hdc
1. WinXP

Virtual on WinXP host=
Same as Ubuntu host.

---

### Post by Kvark on 2007-09-19
Tried the separate /home partition thing, regretted it when I ran out of space on root. Running out of space when there is still space left is stupid. So now I only have two, swap plus root and restore the last backup of personal data after a reinstallation, which only happens when I switch distro.

---

### Post by init1 on 2007-09-19
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         331     2658726    b  W95 FAT32
/dev/sda2             332        9729    75489435    5  Extended
/dev/sda5             332         557     1815313+  82  Linux swap / Solaris
/dev/sda6             558        1933    11052688+  83  Linux
/dev/sda7            1934        3274    10771551   83  Linux
/dev/sda8            3275        4630    10892038+  83  Linux
/dev/sda9            4631        6007    11060721   83  Linux
/dev/sda10           6008        7302    10402056   83  Linux
/dev/sda11           7303        8608    10490413+  83  Linux
/dev/sda12           8609        9729     9004401   83  Linux

I've got lots. 
FreeDOS, Ubuntu, 2 Debian, Vector, Antix, Dream Linux, and GeexboX.

---

### Post by tszanon on 2007-09-19
```
/dev/md0 on / type ext3 (rw,errors=remount-ro)
/dev/sda1 on /boot type reiserfs (rw,notail)
/dev/md2 on /home type ext3 (rw)
/dev/sdc1 on /media/sdc1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdc5 on /media/sdc5 type ext3 (rw)
/dev/sdd1 on /backup type ext3 (rw)
```

---

### Post by Compucore on 2007-09-19
I usually would used two hard disk one partition for the OS like ubuntu on it and the software that I want installed on the primary partition. And the second drive I would use for user accounts and their data on that one. Everyone here has their own preference on this area. There is no wrong way of doing this section here. ANd it is a matter of personal preference on it too. If your able to handle more than four hard drives on a system, they it is better of for you. ANd get it the way you want to do it. I had on my old Aptiva with a 20 and 30 gig hard drive with hoarty hedge hog on it. An just use each hard drive with a partition on each of them. 

Compucore

---

### Post by maybeway36 on 2007-09-19
I'll admit it. I have a lot of partitions.
1. ext3, mounted as Kubuntu / (10 GB)
2. fat32, FreeDOS partition for old games (1 GB)
3. reiserfs, mounted as Kubuntu /home (63 GB)
4. linux-swap of course (1 GB I think)
5. reiserfs, another Linux installation (3.2 GB)
(I installed GRUB to a floppy on the last one so it didn't interfere with the rest of my system)

---

### Post by markp1989 on 2007-09-25
Desktop

i currently have 5 partitions across 2 drives 

Drive 1(40 gb)
part 1 (ext2) geexbox 100mb
part 2 (ntfs) video files >39gb

Drive 2 (80gb)
part 1 (ntfs) windows XP
part 2 (ext3) Ubuntu 
part 3 swap

Laptop :

2 partitions
part 1 (ext3) ubuntu
part 2 swap

---

### Post by Nevon on 2007-09-25
5 partitions across two drives.
Drive 1 (298gb)
Part 1 (ntfs) Windows XP 11,13gb
Part 2 (ntfs) Storage 262.7gb
Part 3 (swap) 3.77gb
part 4 (ext3) Ubuntu 20,5gb
Drive 2 (74gb)
Part 5 (ntfs) Storage 74gb

---

### Post by notwen on 2007-09-25
hda
|-hda1 / (15gb)
|-hda2 /home (64gb)
|-hda3 'swap'

sda
|-sda1 /media/sda1 (250gb)

sdb
|-sdb1 /media/sdb1 (320gb)

easy enough. =]

---

### Post by yatt on 2007-09-25
Something along the lines of:

sda and sdb
RAID1 100MB JFS mounted on /boot
RAID0 1TB JFS mounted on /

sdc
80GB NTFS mounted on /Vista

---

### Post by Arwen on 2007-09-25
Desktop 1:

hda1:Local disk of XP NTFS 30GB
hda2:Data NTFS 25GB
hda3:Arwen(for music and movies) FAT3225GB

sda1: / ext3 for ubuntu 50GB
sda2:swap 1GB
sda3:Downloads(backups and programs etc) 100GB FAT32

Desktop 2:
30GB local disc of XP NTFS
50GB Data FAT32 with 10GB in vmware for suse 10.0

Laptop(for the tiem being :-P) hd=100GB
40GB ufs for pcbsd(generally for trying other distros)
rest is space for data

---

### Post by diskotek on 2007-09-25
6

1 for windows 40 GB
3 for ubuntu :D 120 GB
3 for external hdd, 500 GB

---

### Post by yuri_rage on 2007-09-25
2 - root and swap with plenty of external storage across two 300+GB drives for music/media.

---

### Post by infoseeker on 2007-09-25
Disk 1 (80GB)
/dev/sda1 (30G for XP Home, NTFS)
/dev/sda2 (for Data, etc, ext3)

Disk 2 (80 GB)
/dev/sdb1  (1GB, swap)
/dev/sdb2  (20 GB, Feisty, ext3)
/dev/sdb3  (20 GB, Gutsy, ext3)
/dev/sdb4  (40 GB spare space, ext3)

---

### Post by happysmileman on 2007-09-25
Disk /dev/hda: 80.0 GB

/dev/hda1   *           1        6374    51199123+   7  HPFS/NTFS //Windows XP
/dev/hda3            6375        9729    26949037+   5  Extended //I think that just means the below entries are on extended partition?
/dev/hda5            6375        9453    24732004+  83  Linux //Ubuntu
/dev/hda6            9454        9729     2216938+  82  Linux swap / Solaris //Swap

Disk /dev/sda: 250.0 GB

/dev/sda1   *           1           5       40131   83  Linux //Gentoo /boot (isn't used but not bothered to delete such a small partition)
/dev/sda2               6         130     1004062+  82  Linux swap / Solaris //Gentoo swap
/dev/sda3             131        6210    48837600   83  Linux //Gentoo
/dev/sda4            6211       11048    38861235    b  W95 FAT32 //Music and Black Books box set, and at times backup

The rest of my 250GB drive is unused (almost two-thirds of it... Don't have much of a use, but unused space can always be used for new distros or something.)
Also no /home partition, can backup anything I need anyway to external, and don't want to share between ubuntu and gentoo anyway

---

### Post by koenn on 2007-09-25
> **curiousnoob said:**
> I saw this webpage ( [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) ) and was thinking the best option seemed to be the 4th option down.  The one with 5 partitions.  
My question is what size should the various partitions be and can this all be done with the live cd?
That one is indeed a good layout for a multiboot system. Sizes depend on your needs, but follow the guidelines in the article, or try
10-15 GB Windows (NTFS) system 
5-10 GB Ubuntu /
small /home  ( few 100mb - 1GB) - it will only hold your user settings/preferenses for Ubuntu, assuming you store all other data on the FAT32 partition (that you can also reach from Windows)
the rest : data - as big as possible. 

other schemes only make sense if you have special requirements for your computer, and understand their consequences re. the filesystem, etc. so you can accomodate for them by tweaking the partitioning scheme. 


Here's mine:
```

Filesystem            Size Used Avail Use% Mounted on
/dev/hda1             4.8G  3.4G  1.2G  74% /
/dev/hda2             swap
/dev/hda3              59M   28M   28M  50% /boot
/dev/hda5              29G   26G  2.2G  93% /home
/dev/hda6              41G   37G  2.9G  93% /srv

```

/boot is a leftover from some experiments, 
/srv is what i use for data that doesn't belong to a specific user - a collection of CD images, backups from config files, downloads, ...
I keep those seperate because it sorts of reflects the wauy i partition my server(s) : users have a /home, but data (database, web pages, file shares) go under /srv  (in stead of the more usual /var, where they get mixed with log files, spools, ..)

---

