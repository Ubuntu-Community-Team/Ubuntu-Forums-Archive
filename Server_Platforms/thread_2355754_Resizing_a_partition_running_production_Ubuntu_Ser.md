---
title: "Resizing a partition running production Ubuntu Server"
date: 2017-03-16
forum: Server Platforms
---

### Post by whirlmind on 2017-03-16
While installing Ubuntu Server edition from a Ubuntu Live CD, I had chosen the 'Use entire disk' option. On top of Ubuntu, I installed Redmine, MySql etc. and the application is in production. (It's a very small two member team, so the word 'production' may be a big one to use). I am a novice to Ubuntu Server, I adopted it as a quick means to using Redmine. If it matters, I also have a Lubuntu Desktop and WebMin installed on the server. (Yes, I know desktops shouldn't be installed on servers, LoL). 
Now I am assuming Ubuntu Server must have created a single partition spanning the whole disk. I would like to reduce that partition in which Ubuntu Server is installed, create another partition in the same disk unrelated to the Ubuntu Server so that I can use the new partition for backups storing partition image, other docs etc. 
For resizing, I usually boot from any Linux CD that has Gparted (such as Puppy) and go about the shrinking, new partition etc. In this case, will the shrinking of the Ubuntu Server partition, affect the Ubuntu installation or the application ? It shouldn't happen that Ubuntu Server sees the reduced size when it is booting and then go bonkers trying to resolve it and mess up the server installation. I don't want to be in a position where I have to go through the whole installation process once again. 
I shall take a disk image using clonezilla/PING and backup the Mysql database and redmine application user files. 
But is there anything else I need to worry about or take precaution before I go about the resizing the Ubuntu Server partition ?

---

### Post by howefield on 2017-03-16
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by LHammonds on 2017-03-16
I have never shrunk a Linux partition so I wouldn't know.  I do know it isn't as easy as seeing the partition as a bunch of free space since the OS has the right to place data anywhere inside the partition it wants so it would need to be much smarter than simply changing the size of the partition.

For future reference, you might want to review my notes on installing an Ubuntu Server on how I configure partitions for a true production server...which allows you to keep unused space available for other reasons and only increase when needed.

LHammonds

---

### Post by darkod on 2017-03-17
You will have to shrink the filesystem first. I have never done partition shrink too, but the way I understand it, the filesystem is "always at the front of the partition". Which means if you have a partition of 100GB and you shrink the filesystem to 50GB, and you have only used 25GB of those, the 25GB can be where ever in the 50GB but they can never be out of them. So in theory it would be safe to shrink the partition "cutting out" the last 50GB from it.

But that is how I understand the theory, I have never done it either.

Using Gparted from live mode can also help and I believe it does both operations for you in one (shrink the FS and shrink the partition).

PS. Another thing to consider is do you actually need this risky operation of shrinking the partitions. You said you want to use the new partition for storing backups, other docs, etc. If that's backups from the same machine, storing it on the same disk/machine is not a backup anyway. If the disk goes, your backup file is also gone. As for docs, you can probably manage to store them elsewhere too, or inside the ubuntu server itself without shrinking the partition.

---

### Post by whirlmind on 2017-03-17
@LHammonds : and @darkod :
Thank you for all the inputs. Shall keep those in mind.

---

