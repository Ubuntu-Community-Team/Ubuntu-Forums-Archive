---
title: "Why Partition?"
date: 2007-05-15
forum: The Cafe
---

### Post by Mooose on 2007-05-15
Why is it necessary to partition a disk for a Linux install?  I don't really see any advantages over just using one partition.  It just seems a little strange to me.  Anyone know if there are any concrete advantages?

---

### Post by xyz on 2007-05-15
Avoid data loss by creating a home partition, for instance.

---

### Post by heimo on 2007-05-15
> **Mooose said:**
> Why is it necessary to partition a disk for a Linux install?  I don't really see any advantages over just using one partition.  It just seems a little strange to me.  Anyone know if there are any concrete advantages?

Advantage of using more than one partition is that you can have all your personal files on a separate partition. It makes fresh installs easier. There are other benefits too, but one could also argue that sometimes it's just easier to have one big single partition with everything on it.

---

### Post by xyz on 2007-05-15
Yesterday I installed Feisty on my brother-in-law's box and he insisted on having one single partition...I said ...do as you wish!

However he has an external drive where saves everything important!

---

### Post by LaRoza on 2007-05-15
There are many reasons for partitioning, I have two hard drives, (SATA internal) and have a partition on my Vista drive, 9 Gigs FAT32, to make it very easy to share things between Vista and Ubuntu. I have Ubuntu on one partition.

---

### Post by mjitkop on 2007-05-15
+1 for separate partition for /home. :)

I just updated from Feisty Fawn to Ubuntu Studio and I did a fresh install by replacing (formatting) my root partition. Since my /home partition was separate from my root, I was able to keep all my data and Ubuntu Studio sees it without any problems. :guitar:

---

### Post by EndPerform on 2007-05-15
At the very least, you should have a / and a swap partition, although if your box has a lot of ram, you *might* be able to go without a swap partition.  But, as others have said, having a separate /home partition is nice, especially around upgrade time.  Speaking of, I need to back up my laptop and rebuild it with a /home partition at some point :)

---

### Post by starcraft.man on 2007-05-15
> **Mooose said:**
> Why is it necessary to partition a disk for a Linux install?  I don't really see any advantages over just using one partition.  It just seems a little strange to me.  Anyone know if there are any concrete advantages?

You do realize windows and macs are partitioned too... often times with multiple drives (for example my moms acer had 3 drives, one for XP, one for programs and a third for Data). Its not something alien that Linux does to confuse people. As to why, there are several reasons. You want Swap file partition to use for when your doing memory intensive tasks running out of ram will slow you down INCREDIBLY, you want a home partition so that you keep your data separate. Not to mention lots of other things... just for example, I partition like this:

10 GB XP
10 GB Ubuntu
2 GB swap file
80 GB Home partition

External Drive:
200 GB DATA Fat32 for XP and Ubuntu
20 GB for Backup Images

I like things nice and organized :)

---

### Post by SeanHodges on 2007-05-15
My usual approach is to have the following:

/                   - 20GB, although this is about double what I usually need, it reduces risk 
/boot            - 50MB, this is again much more than needed, but who's going to miss 50MB these days?
/tmp             - 1GB
/home          - All remaining disk space
(swap)


Lots of people have different opinions on partitioning, some think things should be separated further, some less... Heres my reasoning for this approach:

- Root should be separate from user files, this makes it easier to reinstall without losing personal data, and avoids you crashing the system when you use up all available disk space with downloads etc.

- Boot should be separate from system and user files, as it is required to start up the system. If you corrupt your root filesystem you can still boot other operating systems on your computer... you can also easily recover the system by booting up a live CD, mounting the tiny boot partition quickly and blatting over it with a new Grub configuration, all without the risk of trashing the root filesystem.

- Your /tmp directory is as risky as your /home directory, as normal users can write to it. Separating it gives some security against large temporary files being written and using up all the disk space.

- Some people believe each user should have their own partition, so a partition for /home/user1, another one for /home/user2, etc... But there are easier ways of doing this with quotas, which also make it easier to move allocated space around.


Hope this is of some help

---

### Post by ssam on 2007-05-15
when you do upgrades or reinstalls having you home on a separate partition is no substitute for having a backup.

also sharing a home folder between installs could be messy if they have different versions of software. the older version may not know how to read the newer versions config files.

on my desktop i just have partitions for / and swap (aswell as one for testing dev versions of ubuntu, and one for mac os x (not that i use that much)). on my jukebox/server i have /usr on a separate partition (on a ide disk) so that it can boot from a 1GB compact flash.

---

### Post by SeanHodges on 2007-05-15
> **ssam said:**
> when you do upgrades or reinstalls having you home on a separate partition is no substitute for having a backup.

Agreed, it is not a substitute.

However, it is an extra security measure. I have used this approach for many years now and find it very effective. In the rare case that an application misbehaves once an upgrade is performed (because the data files in the home directory are out of date) I find purging the data files and reinstalling the application will restore the sanity of the application quickly and efficiently. Leaving me with just one application to reconfigure, instead of all of them.

I would never recommend that someone upgrades or reinstalls without making a physical backup of all their important data first... Photos, documents, etc... However most people don't have the resources to back-up 300GB of music, films and VM images, having a separate partition makes this possible.

---

### Post by forrestcupp on 2007-05-15
I understand the point about having your personal /home on a separate partition for reinstalls/upgrades, etc.  But the way I see it is once you partition your drive, you're stuck with that amount of space.  If I partition my root too small and my home too big, I might run out of space to install software and have too much space for my personal files.  If I have all of / on one partition, I don't have to worry about space sizes.

You should have swap on a separate partition, though.

---

### Post by B0rsuk on 2007-05-15
> **Mooose said:**
> Why is it necessary to partition a disk for a Linux install?  I don't really see any advantages over just using one partition.  It just seems a little strange to me.  Anyone know if there are any concrete advantages?

Why brush your teeth ?

---

### Post by az on 2007-05-15
> **Mooose said:**
> Why is it necessary to partition a disk for a Linux install?  I don't really see any advantages over just using one partition.  It just seems a little strange to me.  Anyone know if there are any concrete advantages?

By default, only a root and a swap partition are created.  Using a swap partition instead of a swap file is faster by an order of magnitude.  The only other time you need to create another partition is when you would want to dual boot.

Creating aseperate home partition is not really necessary.  It's a fun experiment, but there are better and easier ways to back up your data.  There are times when you don't want to share configs between two linux desktops, especially when you are running different versionf of apps which configure things differnetly, but use the same file.

---

### Post by SeanHodges on 2007-05-16
> **forrestcupp said:**
> I understand the point about having your personal /home on a separate partition for reinstalls/upgrades, etc.  But the way I see it is once you partition your drive, you're stuck with that amount of space.  If I partition my root too small and my home too big, I might run out of space to install software and have too much space for my personal files.  If I have all of / on one partition, I don't have to worry about space sizes..

You're always stuck with a certain amount of space. The Operating System and applications are going to need disk space to exist and also to run. The advantage to a single partition is that you don't need to spend a much time at the installation process, calculating how much space you might need, but the disadvantage is that you DO need to worry about space sizes, as running out of disk space means that not only can you not download/install/create anything... but you will also find your system slows down, malfunctions, and in the worst cases fails to start up entirely.

My first O/S installs used to be a single partition, but even before I switched to Linux I was using a separate partition for my My Documents in Windows, just so that things didn't blue screen on me merely because I downloaded a CD image that exceeded my remaining disk space.

If you do partition things as I've described, you really need to think carefully about how much you're allocating, but if you do it right first time you don't ever need to worry about it again, and the entire system benefits from it.

At this point, I just want to clarify that I don't think people who don't partition their filesystem to be wrong, I'm just clarifying why I do it so people get the full picture.

---

### Post by forrestcupp on 2007-05-16
> **SeanHodges said:**
> You're always stuck with a certain amount of space. The Operating System and applications are going to need disk space to exist and also to run. The advantage to a single partition is that you don't need to spend a much time at the installation process, calculating how much space you might need, but the disadvantage is that you DO need to worry about space sizes, as running out of disk space means that not only can you not download/install/create anything... but you will also find your system slows down, malfunctions, and in the worst cases fails to start up entirely.


I don't think you understood what I was saying.  If I have a 40 GB harddrive, and at installation I partition 10 GB for root and 30 GB for home, I'm stuck with that.  Maybe at first I think I'm going to be mainly doing videos and not installing a lot of programs so I need the extra home space.  But then my needs change, I quit doing video work and start installing lots of apps/games.  When I find out almost everything I install goes to root, I realize I didn't partition enough root space, but it's too late.

If I put everything but swap on one partition, it doesn't matter.  My root and home sizes are dynamic and changeable.  I don't have to worry about how much space each one takes up; I only have to worry about how much space everything all together takes up because of the obvious 40 GB limit.

---

### Post by heimo on 2007-05-16
> **forrestcupp said:**
>   But then my needs change, I quit doing video work and start installing lots of apps/games.  When I find out almost everything I install goes to root, I realize I didn't partition enough root space, but it's too late.

Then you can resize your other partition, make a new one to the empty space and move your /usr or /var or any other part of your system to the new partition, or buy a new disk for that. It's really quite flexible. Of course you could also use "dynamic disks" - logical volume management (LVM) to allocate disk space dynamically.

Not trying to argue here, just saying that there are many ways of partitioning and everyone is free to do as they wish.

---

### Post by saulgoode on 2007-05-16
There are only a couple of reasons I can think of for having more than one partition+SWAP -- but the reasons are sufficient to justify them for me.

As mentioned, the first is dual-booting (or multi-OS booting). Having an extra partition on your machine is very useful if you wish to try out different distros; it is also useful for having a "pristine" version of your favorite distro if you wish to package different software for contribution to repositories (by "pristine", I mean that you only have the bare minimum distribution so that you won't miss any dependencies). Even if I don't intend to dual boot, I always have an extra partition for this purpose. I might even mount it as /home but I still have the option to, at a later date, move /home over to the root partition to make the partition available.

The other reason for multiple partitions is if you wish to implement software RAID. If you have more than one harddisk available, you can pair up partitions between them to either increase the reliability of your storage or increase the access speed.

I always partition my drives into four partitions. This allows me the flexibility to restructure things later if I wish.

---

### Post by dca on 2007-05-16
For how Ubuntu desktop defaults, I think it's fine.  I never dual boot w/ another OS (I'm monogymous w/ Ubuntu) so I can't really offer any other benefits on the desktop side.
 
On the server or enterprise side, that's where it comes into play.  Linux is basically a multi-user, multi- this, and multi-that OS.  That's where you see most Linux distro(s) outside of the Desktop vers of Ubuntu separating out the /home directory to a separate partition.  Especially for Samba, most server installs default to having the share(s) saved on the /home directory.  Say if the server is conncted to TSM or some other kind of b/u manager, this makes it easier.  Depending on how your enterprise deals w/ data redundancy and other factors is how you set-up your partitions.
 
Bottom line if you use Linux on the desktop or dual-boot, a partitioning scheme is quite simple.  Basically use whatever the installer says it defaults to...

---

### Post by 3rdalbum on 2007-05-16
I've always run with just / and swap.

I decided to do a clean install of Ubuntu to go from Dapper to Feisty. I backed up my home directory, it took about 15 minutes. I backed up my Windows partition, which took a similar amount of time.

After the installation, I just copied my home directory back over.  15 minutes later, a reboot did exactly the trick.

I don't worry about filling up the / partition - if you do, you can always use a Live CD or usually even the recovery mode to delete excess files; and I always save big files to my external drive anyway.

---

### Post by matthinckley on 2007-05-16
> **B0rsuk said:**
> Why brush your teeth ?
not very helpful, but made me laugh! :)

---

