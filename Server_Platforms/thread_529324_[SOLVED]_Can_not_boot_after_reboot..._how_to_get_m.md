---
title: "[SOLVED] Can not boot after reboot... how to get my data??"
date: 2007-08-19
forum: Server Platforms
---

### Post by TgT on 2007-08-19
I`ve been running Ubuntu Dapper server as for a long time now on my old 500mhz and 8gb IBM disc. Few days ago PC suddenly rebooted and after that It didnt boot anymore. 
It says Error 17 ...
I tried many things to solve grub thing and nothing helped, also tried super grub tools, disc is OK and partitions are still there. 
Now, how on earth can I get some data of that disc? 
I need mysql db... :(

---

### Post by jpkotta on 2007-08-19
Boot with a Live CD, mount the disk, and copy it somehow (e.g. scp, install another disk, USB disk, ...).

---

### Post by TgT on 2007-08-19
I did that but somehow it didnt work, dunno what was the pro0blem so I tried it again. I used Xubuntu liveCD and tried to mount but i got a message saying
> 
mount: wrong fs type, bad option, bad superblock on /deb/hdb1,
missing codepage or other error

I tried also dmesg | tail and output was
> VFS: cannot find and ext2 filesystem on hdb1
Also happens if i try ext3 ...
Then i ran GParted which showed me *filesystem unkown*?
hm...
Also, i tried fdisk -l and output was 

/dev/hdb1* id/83   system/Linux

right...

I attached disc on my main PC and used partition magic. For this disc it says Linux/Other and my other linux partitions are showed cleary as ext2 or ext3. 

Now i dont have any idea how to go further with this...

---

### Post by koenn on 2007-08-19
You may have a bad superblock. This is where info about the filesystem type is stored. grub error 17 means that grub doesn't recognise the filesystem, and your mount failures seem to confirm this - unless you're trying to mount with a wrong filesystem type. You really should check this. 

There are alternative superblocks present on the disk so you could try mounting that partition (from a live cd session) with something like

```
mount sb=n  /dev/sdaX   /mnt
``` OR 
```
mount sb=n  /dev/hdaX   /mnt
```
where n is the block number of the alternate superblock. 

    * For filesystems with 1k blocksizes, a backup superblock can be found at block 8193
    * For filesystems with 2k blocksizes, at block 16384
    * For 4k blocksizes, at block 32768.

You can also try any one of the following commands to determine alternative-superblock locations:
```
# mke2fs -n /dev/sda3
```
OR
```
# dumpe2fs /dev/sda3|grep -i superblock
```


you can also try to repair the broken filesystem by using an alternate superblock : ```
e2fsck -f -b 8193 /dev/sda3
```
This is not recommended, because you'd be writing to the filesystem that you want to recover data from - try mounting it first to copy your data, or make an image of the disk (eg with dd ) so you can fall back if anything goes wrong. 

sources: 
man mount
man dd
[http://www.cyberciti.biz/tips/mounting-with-an-alternative-superblock.html](http://www.cyberciti.biz/tips/mounting-with-an-alternative-superblock.html)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://www.linuxjournal.com/article/193](http://www.linuxjournal.com/article/193)


Take your time to read the articles - you need some context, you don't want to make things worse now by blindly copying commands here ...

and consider making backups in the future  :)

---

### Post by TgT on 2007-08-26
Hm.. I've been away for a while.

fdisk -l says this
> root@ubuntu:/# fdisk -l

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         981     7879851   83  Linux
/dev/hdb2             982        1027      369495    f  W95 Ext'd (LBA)
/dev/hdb5             982        1027      369463+  82  Linux swap / Solaris


mke2fs -n /dev/hdb1 this

> 
mke2fs 1.39 (29-May-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
985760 inodes, 1969962 blocks
98498 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2017460224
61 block groups
32768 blocks per group, 32768 fragments per group
16160 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632


So lets go mount?

Tried all superblocks with this line
> /dev/hdb1 /mnt/disc/ -t ext3 -o sb=n
Ofc n is a nuber from above eg. 98304 
I tried with -t ext2 too. Nothing happend
Dmesg says
>  
VFS: Can't find an ext2 filesystem on dev hdb1.
 VFS: Can't find ext3 filesystem on dev hdb1.

for all mounts i tried. How its not there if fdisk recognize it? :p

What else can i do? :)

---

### Post by TgT on 2007-08-26
Ok, i did it wrong :)

I get 
> 
EXT2-fs: corrupt root inode, run e2fsck
EXT3-fs: invalid journal inode.


Hmm

---

### Post by TgT on 2007-08-28
Ok.

First i did a copy of my hdb1 partition with dd
Then i ran
> e2fsck -y -f -v /dev/hdb1
and waited a bit. After that i was able to mount partition, copied files i was looking and viola. Mission done.
Now, new fresh instalation coming up :p

---

### Post by koenn on 2007-08-29
congrats.

---

