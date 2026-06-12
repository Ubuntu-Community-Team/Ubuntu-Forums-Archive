---
title: "( / ) or ( /, /home) or ( /boot, /, /home)"
date: 2009-11-26
forum: The Cafe
---

### Post by renkinjutsu on 2009-11-26
Just wondering what the general consensus is.. I'm a (/, /home) kinda guy, but i did a /boot / /home install for Karmic.

What do you guys think? Pros and cons?

Discuss.

---

### Post by LowSky on 2009-11-26
I just do /home and /

never saw the point of /boot

---

### Post by bruno9779 on 2009-11-26
I do /home and / as well.

---

### Post by gletob on 2009-11-26
Well...

```

glenn@glenn-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce06f85c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12465   100125081    7  HPFS/NTFS #Windows 7 Ultimate
/dev/sda2           12466       12530      522112+  83  Linux  #Ext2 /boot
/dev/sda3           12531       35389   183614917+   5  Extended
/dev/sda4           35571       38913    26852647+  83  Linux #Ext4 Arch Linux
/dev/sda5           12531       17100    36708493+  83  Linux #Ext4 /
/dev/sda6           17101       34997   143757621   83  Linux #Ext4 /home
/dev/sda7           34998       35389     3148708+  82  Linux swap / Solaris

```

---

### Post by renkinjutsu on 2009-11-26
i made a /boot partition when i installed karmic.. it doesn't really do much.. In fact, it actually decreased boot-time, since fsck checks 3 partitions for bad blocks.

---

### Post by Marlonsm on 2009-11-26
I have the default one, only /.
But I think that the next time I do a clean install it will be / and /home, so when I upgrade I can keep my /home even with a clean install.

---

### Post by ZankerH on 2009-11-26
/boot, /home, /tmp/, /usr on separate partitions for all server boxes. Separate and minimal (a few GB) /, /home and /boot partitions on workstations, with separate huge partitions for data storage.

---

### Post by gashcr on 2009-11-26
> **Marlonsm said:**
> I have the default one, only /.
But I think that the next time I do a clean install it will be / and /home, so when I upgrade I can keep my /home even with a clean install.

That's the reason I do / and /home. This way I can be worry free with clean installs :D

---

### Post by drs305 on 2009-11-26
/
/data

Before a clean install, I create a separate /home. Install, then remove it. Takes about 3 minutes.

---

### Post by MaxIBoy on 2009-11-26
On this laptop, I have (in this order)
/
/home
/opt
The theory behind /opt is that I could dual-boot and share openoffice accross multiple OSs, saving space, but so far that hasn't been needed. If I had cause to redo my partition table, I would likely drop it.

On my desktop (currently packed away,) I have
/ (32 bit Ubuntu)
/home
/ (64 bit Ubuntu, planning to install Arch or Sidux here.)

---

### Post by gn2 on 2009-11-26
Apparently while installing Ubuntu it's possible to preserve an existing /home directory even if it's not on a separate partition these days.

Haven't tried it myself though because I prefer the tried and tested separate /home partition.

---

### Post by Psumi on 2009-11-26
one file system for the whole thing. Do not want it any more complicated.

---

### Post by Pogeymanz on 2009-11-26
I have /boot, /, /var, /home.

/var holds my custom compiled packages and package cache in case an upgraded package is somehow regretted. It could easily fill up if I don't pay attention and I would hate if that filled up my / partition.

---

### Post by Xbehave on 2009-11-26
/boot - so i can change distros/dual boot/mess everything up
/home - see (1) and it's always good to keep data seperate (+noexec)
/

I also have a seperate
/opt - sharing custom installed programs e.g firefox betas
/tmp - mounted to ram (noexec)

I once went further and have /usr (mounted ro) and /var (mounted noexec) but I dunno if it was worth it.

---

### Post by Pogeymanz on 2009-11-26
> **MaxIBoy said:**
> 
/opt
The theory behind /opt is that I could dual-boot and share openoffice accross multiple OSs, saving space, but so far that hasn't been needed. If I had cause to redo my partition table, I would likely drop it.

That's very interesting. So, you would mount this /opt partition for every Linux distro you have installed? Does that actually work or do you have to install Openoffice every time?

---

### Post by RATM_Owns on 2009-11-26
/ for everything.

---

### Post by Xbehave on 2009-11-26
> **Pogeymanz said:**
> I have /boot, /, /var, /home.

/var holds my custom compiled packages and package cache in case an upgraded package is somehow regretted. It could easily fill up if I don't pay attention and I would hate if that filled up my / partition.
Why not use /usr/local/ and /opt, like the rest of the world? That way /var only contains **var**iable data

---

### Post by Xbehave on 2009-11-26
> **Pogeymanz said:**
> That's very interesting. So, you would mount this /opt partition for every Linux distro you have installed? Does that actually work or do you have to install Openoffice every time?
I do that /opt is great for anything that is not maintained by your package manager. It works fine, I ran the same firefox 3.5 from opt in ubuntu, debian and fedora until fedora caught up. I also keep
asciiportal-linux64  and cisco-vpnclient (has kernel modules so not very portable) in there

---

### Post by ibuclaw on 2009-11-26
Unencrypted installation:  /, /home and swap
Encrypted installation: /boot, { /, /home and swap }

---

### Post by nrs on 2009-11-26
/, /home. 

/ is expendable to me. it doesn't matter, if I lose something during an upgrade, or by switching to another distribution, I can just install it again using the package manager. I can't do that with my personal files. So they live on their own partition free from the thought of / breakage.
[U][I][B]
[COLOR=DarkOrange]Edit[/COLOR][/B][/I][/U]
/, /home, and /boot when using an lvm with /.

---

### Post by Pogeymanz on 2009-11-26
> **Xbehave said:**
> Why not use /usr/local/ and /opt, like the rest of the world? That way /var only contains **var**iable data

Well, I like to use JFS as my main filesystem, but reiserfs is supposed to be better with small data and compiling and such. So I compile my data in the same place where the variable data is, so I can use reiserfs on one big partition.

---

### Post by toupeiro on 2009-11-26
I tend to always make a /tmp partition on all of my systems.

When most applications barf, they barf in the /tmp directory.  If an application starts to do this without my knowledge, I would rather it fill up the /tmp partition than my / partition.

For that matter, I also make a /boot at minimum.  Sometimes I will make others as is necessary.

---

### Post by baizon on 2009-11-26
> **bruno9779 said:**
> i do /home and / as well.

+1 :)

---

### Post by lovinglinux on 2009-11-26
I have / and /home, although my home partition is very small and only holds configuration files. All my personal documents and folders are stored on two other partitions that I mount under home and create symlinks to them inside home.

I also would like to understand the benefit of /boot

---

### Post by Xbehave on 2009-11-26
> **Pogeymanz said:**
> Well, I like to use JFS as my main filesystem, but reiserfs is supposed to be better with small data and compiling and such. So I compile my data in the same place where the variable data is, so I can use reiserfs on one big partition.
why not have /usr/local as reiserfs (perhaps uning a binding mount point for now to avoid repoartitioning) then, obviously it's your system but running programs out of /var just seams '*wrong*'.

p.s is reiserfs really that good for compiling? i've found resier to use more CPU so i'd have thought it was worse for compiling.

> When most applications barf, they barf in the /tmp directory. If an application starts to do this without my knowledge, I would rather it fill up the /tmp partition than my / partition.
Doesn't /tmp clear itself on reboot anyway? I used to do the same but now i mount /tmp to ram and added the space i had for /tmp to swap

---

### Post by blueshiftoverwatch on 2009-11-26
/ = Ext4
/home = ReiserFS

---

### Post by Confuzius on 2009-11-26
I had a separate /home partition once, but dual booting two distros with the same username screwed it all up somehow. 

Is there a way to do that safely with multiple distros sharing the same username or should a shared /home have different user names like "confbuntu" and "confdora"

---

### Post by blithen on 2009-11-26
> **gashcr said:**
> That's the reason I do / and /home. This way I can be worry free with clean installs :D

Im a /home, / Guy too. And for this reason!

---

### Post by ssam on 2009-11-26
everything on /. the ubuntu installer can do a clean install preserving /home. just use the manual partitioner and dont tick the format box.

actually i usually have a /data that is a big partition on another disk. eg my desktop has / (including home) on a WD raptor, and /data is a 1TB drive, my beagle board has / (including /home) on an SD card, and /data on a 400GB disk.

i use /data to hold big things like music, iso files, virual disk images. stuff that either does not need backing up, or only needs backing up occasionally. home folder needs daily snapshots (rsnapshot).

sharing /home across distros is likely to lead to trouble. eg if the distros have different versions of a program both messing with the same config file.

---

### Post by The Real Dave on 2009-11-26
/ and /home. For Ubuntu anyways. All my disks are partition madness :) What are the benefits of having a seperate /boot?

---

### Post by Sam on 2009-11-26
[LIST=1][*]/boot
[*]swap
[*]/
[*]/home
[/LIST]

---

### Post by Exodist on 2009-11-26
I have my system on my root file system / and my /home folder on a totally separate drive all together.

---

### Post by Tibuda on 2009-11-26
I only have /, /home and swap, but I would like to know the benefits of a /boot partition and how much space do you have on /boot.

---

### Post by tad1073 on 2009-11-26
/boot, /, /usr, /home, /var

---

### Post by szymon_g on 2009-11-26
"other, please specify"

/swap - not too big, 500mb is enough (used mostly for hibernating)
/boot on ext3 - sure, grub2 can boot from ext4, same as patched grub- but it is not always applicable. circa 100mb

/ - small, 3gb, ext4
/var - 3gb, ext4- it is better to have it seperated, just in case of some over-reacting applications (i.e. flooding to rsyslog). of course- you still have to have logrotate

/usr - 12gb, ext4- all default stuff goes there

/home/users/username - i always set up system to use it instead of default /home/username- its much easier to manage (for me).

/home/services/ - for services like apache, ftp etc
/home/games/ - for games that aren't installed from repo (like ETQW)
/home/shared/ - as name suggests, for shared data (shared between users)

those 4 directories can be located on one partition (ext4 for me), or seperated- that depends from importance of selected services (is it rather server or rather desktop? does it works in well networked environment? etc)

/tmp in ramdisk, as tmpfs
/var/run in ramdisk

---

### Post by Barrucadu on 2009-11-26
_Ext2:_
/boot

_JFS:_
/
/var
/home

_tmpfs:_
/tmp
~/tmp/downloads
~/tmp/misc
~/tmp/uzbl
~/tmp/vlc

---

### Post by almufadado on 2009-11-26
I install as "/" and "/home" and "swap".

Then a have a different drive, a "data" drive to where i move the default folders (doc's images, etc).  

As I intend to test some features in of some other distros, I will be considering go "/boot" too.

I think this will help :
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

---

### Post by jimi_hendrix on 2009-11-26
I have a / and a /home since i do reinstalls often (i like testing distros), i had a /, /home/ and /boot on fedora 10 though, since grub didnt support ext4 at the time and would not read your /boot if it was ext4

---

### Post by beercz on 2009-11-26
/ and /home for me.

Thank you and goodnight!

---

### Post by Firestem4 on 2009-11-26
I actually have everything under /, and swap as a separate partition.

---

### Post by Yes on 2009-11-26
/, /home and /boot are ext3.  /var is reiserfs.

---

### Post by renkinjutsu on 2009-11-27
> **danielrmt said:**
> I only have /, /home and swap, but I would like to know the benefits of a /boot partition and how much space do you have on /boot.

i use 100MB for my /boot partition, but i could do with a little less space too..

---

### Post by PurposeOfReason on 2009-11-27
I have a few drives.
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d350ef6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027226

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13        6375    51097600    7  HPFS/NTFS
/dev/sdc3            6375        6381       48195   83  Linux
/dev/sdc4            6381        7783    11267728+  83  Linux

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1          30      240943+  83  Linux
/dev/sdd2            1276        1785     4096575   82  Linux swap / Solaris
/dev/sdd3            1786       91201   718234020   83  Linux
/dev/sdd4              31        1275    10000462+  83  Linux

Partition table entries are not in disk order


```I prefer seperate storage partitions instead of putting stuff in home.

---

### Post by thegreenblob on 2009-11-27
I use /, /boot, and /home, simply cause it's default in Arch. I don't really know any advantage of having a /boot, but I don't know of a con either.

However having a seperate /home partition is really useful if you want to keep all your files and settings while reinstalling or upgrading, or installing a new distro.

---

### Post by Ylon on 2009-11-27
/ and swap.

---

