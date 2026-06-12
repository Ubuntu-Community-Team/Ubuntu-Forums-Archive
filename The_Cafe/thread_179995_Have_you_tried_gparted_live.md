---
title: "Have you tried gparted live?"
date: 2006-05-21
forum: The Cafe
---

### Post by catlett on 2006-05-21
Has anyone used gparted live? I just found it. [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828) I can't say enough good things. The best part is you don't have to boot into a linux distro's live cd to run gparted any more (at least I don't. that's how I used to do it)
I almost always use Partition Magic from windows to make partitions. This is one up on that. PM would reboot windows and launch a batch file before windows  mounted the drive at start up. Gparted being on a live cd does everything right there  from it's gui.
Just thought I'd pass it along. It worked great for me plus it's open source aka free:D

---

### Post by Sef on 2006-05-21
> Has anyone used gparted live?

I have and have recommended it in a number of my posts.  I've had some partition problems before that GParted took care of, so I could install Ubuntu.  Here's the link for the GParted site.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by catlett on 2006-05-21
[QUOTE=Sef]I have and have recommended it in a number of my posts.  I've had some partition problems before that GParted took care of, so I could install Ubuntu.  Here's the link for the GParted site.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")[/QUOTE]
I missed your links. I wish I hadn't because I was always getting errors when I tried to further partition my hard drive. Gparted live just made two more partitions, no errors or problems. 
There should be a direct "ask Sef" link around here somewhere:D

---

### Post by junior aspirin on 2006-05-21
i downloaded a few days a go, but havnt used it yet. im glad to hear good things about it. im about to do some hardcore disk reorganising soon, and gparted is exactly what i need. it involves replasing a hard disk with a much larger one then resizing a partition, and partitioning the new drive, then reinstalling dapper and xpee. ooo the hours of fun... ](*,)

---

### Post by K.Mandla on 2006-05-21
Ditto the OP. That GParted Live CD should be in every computer fan's collection. It saved my skin just a few weeks ago, redrawing a partition to make space for a dual boot (I had tinkered with Dapper again :rolleyes: ). 

If you know what it means to partition a drive, you can run it -- and probably ought to have it. (And it's not a big download, either.) :)

---

### Post by confused57 on 2006-05-21
Here's some good screenshots of gparted:

[http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)

This looks like a good system rescue disk:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by AndyCooll on 2006-05-21
Yeah, I've used it. I have a test pc which often has 7 or 8 distros on it. Best way to set up the various partitions etc etc I've found is to use GParted Live

:cool:

---

### Post by Klaidas on 2006-05-21
After reading all these good comments, I guess I'll download it too :)
Dapper install is coming you know :)

---

### Post by sup on 2006-05-21
I tried it but it somehow messed my harddrive a bit, so i had to use cfdisk+mkdosfs/mke2fs instead, which worked quicker (no need to reboot, if you do not mess with the system partition) more flexible (I was able to name volumes and set root space to zero for ext3 filesystem (gave me something like 10GB) - something gparted does not allow to my knowledge) and more reliable to me. But then again, I suspect the disk to be physically broken, so it might be the cause of my troubles. 
As to the Partition Magic, it once messed my harddrive when I tried to squeeze my ext3 partition with home on it I had to do some awful hacking that took me all-day to be able to boot either to windows or to linux. Since then, I do not believe anything with gui that has to do anything with partitions. But then again, I used to be a little bit reckless when it came to partitioning.

---

### Post by catlett on 2006-05-21
[QUOTE=sup]I tried it but it somehow messed my harddrive a bit, so i had to use cfdisk+mkdosfs/mke2fs instead, which worked quicker (no need to reboot, if you do not mess with the system partition) more flexible (I was able to name volumes and set root space to zero for ext3 filesystem (gave me something like 10GB) - something gparted does not allow to my knowledge) and more reliable to me. But then again, I suspect the disk to be physically broken, so it might be the cause of my troubles. 
As to the Partition Magic, it once messed my harddrive when I tried to squeeze my ext3 partition with home on it I had to do some awful hacking that took me all-day to be able to boot either to windows or to linux. Since then, I do not believe anything with gui that has to do anything with partitions. But then again, I used to be a little bit reckless when it came to partitioning.[/QUOTE]
Are you aware we are talking about gparted "live" not the gparted on the ubuntu system? You run it from a live cd. It is great because your hard drive isn't mounted and it can do everything right there, unlike the gparted Ubuntu version. Plus you don't have to boot a distro live cd to get to gparted, it boots to Fluxbox in xorg on kernel 2.6. The only app is gparted it and starts upon boot.And of course you have to reboot because it is a live cd.

---

### Post by sup on 2006-05-22
> Are you aware we are talking about gparted "live" not the gparted on the ubuntu system? You run it from a live cd. It is great because your hard drive isn't mounted and it can do everything right there, unlike the gparted Ubuntu version. Plus you don't have to boot a distro live cd to get to gparted, it boots to Fluxbox in xorg on kernel 2.6. The only app is gparted it and starts upon boot.And of course you have to reboot because it is a live cd.
Yes, I am aware of that - GParted that is shipped with Ubuntu is not even able to format unmounted external harddrive (it just screws it up, somehow) and it does not give back proper values for volume sizes (I wish I had 350GB drive in my laptop). GParted live CD seems to be much more powerful and it indeed is very neat, but it does not give that much control and for me, it might not work well enough - but maybe it is a problem between the chair and the keyboard.

---

### Post by gmc on 2006-05-22
GParted (live) is nice and I'm sure one of the days I'll probably use it but it seems a little limited right now. I think we can agree that ext3 is considered the defacto standard file system for linux systems these days right? Well gparted can shrink and expand ext3 partitions but it can't move them.

You have 3 partitions, you shink partition 2, you can't move or expand partition 3 to use the space that partition 2 was using.

I'm sure it'll get those features one day but until it does, it's useful but limited.

Gord

---

### Post by catlett on 2006-05-23
Being new to linux I am always in the beginners forum and help mainly with install and grub. People do not (new people that is) know how to get a partitioner. They don't want to buy one to put a free OS on their machine.
In the beginner forum people always ask how to partition. Most of the time the reply is a detailed post about getting Knoppix or another live distro and find qtparted. Or use the partitioner in install etc. 
Gparted live to me is the best newbie partitioner. I probably should have posted "have you new people tried gparted live". It is a small download 30mb instead of 700mb for a live distro. It boots right to the application and has an easy interface.
This shouldn't be used to move partitions and resize because these days an experienced user should be using lvm to manage their disk. Just for this reason. You shouldn't be partitioning data partitoins you should be using lvm to resize your system disk.
So I will posrtscript by saying this is a great tool for someone to partition a hard drive for install or to make a new partition.
After you make your partitions you should be installing with lvm.

P.S. In case someone new stumbles upon this post and is curious about lvm. [http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)

.

---

### Post by se7ensamurai on 2006-05-24
interesting that i just found this thread just now. I screwed up one of my NTFS disks (don't ask how), and used the Gparted live cd, and I'm amazed I'd never heard of it earlier.

now if I can get GRUB back on my winxp drive, I'll be happy!

---

### Post by confused57 on 2006-05-24
[QUOTE=gmc]GParted (live) is nice and I'm sure one of the days I'll probably use it but it seems a little limited right now. I think we can agree that ext3 is considered the defacto standard file system for linux systems these days right? Well gparted can shrink and expand ext3 partitions but it can't move them.

You have 3 partitions, you shink partition 2, you can't move or expand partition 3 to use the space that partition 2 was using.

I'm sure it'll get those features one day but until it does, it's useful but limited.

Gord[/QUOTE]

Wonder if Disk Drake, that is used by PCLinuxOS, can do this?

---

### Post by Master Shake on 2006-05-24
Downloaded it, and I love the thing.  Came in handy during a Ubuntu install at a friend's house.Too bad my DVD Rom drive doesn't like to read burned CD's for some reason.

---

### Post by an.echte.trilingue on 2006-05-24
I don't like having a million CDs with different utils floating around; I prefer them all in one place.

My preference is SLAX:  the CD itself is small (180 MB) and adding functionality is as easy as drag, drop, and double click.  

Just slap in some NVidia drivers, NTFS R/W support, a few utilities like QT parted or whatever else you want, and you have a great tool.

Seriously, people should check out how easy it is to customize!

---

