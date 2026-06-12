---
title: "What's the best filesystem for using Linux as a desktop"
date: 2009-11-22
forum: The Cafe
---

### Post by lightningfox on 2009-11-22
Hello

I want to know what's the best file system for using Linux as a desktop
operating system.

Right now I use ext3 for all my partitions.

I want to know what other people use and which filesystem they think is
best.

---

### Post by Tipped OuT on 2009-11-22
ext4 would be my guess.

---

### Post by jrusso2 on 2009-11-22
Personally I don't like ext, I use JFS or XFS for /home

---

### Post by amingv on 2009-11-22
It really depends on what you'll use your partitions for.

Right now I'm using ext4 on my root partition and ext3 on my home partition; not because I'm worried about data corruption or anything, but because I don't feel like copying several GB of data just to use ext4.

Now I must say I really like ext4 performance, but besides that it's pretty much got nothing (at least not that I've noticed), so I'd say that for general purposes either ext3 or ext4 is fine.

---

### Post by blueshiftoverwatch on 2009-11-22
> **jrusso2 said:**
> Personally I don't like ext, I use JFS or XFS for /home
JFS and XFS are mainly for dealing with large files and /home is generally just a whole bunch of very small files for storing settings.

I use Ext4 for /, ReiserFS for /home, and XFS for my storing my virtual machine hard drives

---

### Post by phrostbyte on 2009-11-22
I use ext4 :!:

---

### Post by sgosnell on 2009-11-22
+1

---

### Post by jrusso2 on 2009-11-22
> **blueshiftoverwatch said:**
> JFS and XFS are mainly for dealing with large files and /home is generally just a whole bunch of very small files for storing settings.

I use Ext4 for /, ReiserFS for /home, and XFS for my storing my virtual machine hard drives

I tend to copy a lot of large video files in my /home.

JFS I use because it so stable.

---

### Post by 1clue on 2009-11-22
Start with a default system.  Modern distributions are fairly well tuned to the people who are attracted to that distribution, and they are run by guys who have a lot more experience than most of us.

Probably the best advice after that is to decide what it is that is taking all the time on your system, and research what is recommended to fix it.  A little bit goes a long way if you take this approach.

First thing, make sure you have enough RAM.  Open the system monitor (assuming you're using the desktop) and make sure that your normal day on the computer doesn't even touch swap space.  Swap is only good if you are going to run out of memory, it lets that rare massive app finish without crashing -- at the expense of a crushing speed penalty.

If you use an app and the disk light is constantly on on your system, then research if there is something else that works better.  For example, Reiser is best for mysql.  I use that for mysql's data directory, but not really anywhere else.  Not because reiser isn't good for anything else (it is) but because other things were more important.

XFS is an archive system for me, because it's very fast with large files and I have battery backup that's better than the norm.

I think one of the great forgotten techniques is to use tmpfs judiciously.  tmpfs is basically a RAM disk.  It's managed by the memory manager, and can be swapped out as necessary.  If you have the RAM, this is awesome.  You can only use it if you don't mind losing all the data in the filesystem when you reboot, though.  However, if you make heavy use of a temp directory, you can make amazing speed improvements by using it.

Anything you do is going to be good for one application and bad for another if you apply it on a large scale, so it's best to plan your system in such a way that any modifications are local.  LVM is nice because you can grow the filesystem and move things around if necessary.

---

### Post by KiraLexi on 2009-11-23
ZFS is nice if you have a distribution that supports it. I remember doing something unspeakably stupid to a Solaris installation once, rebooting... and just selecting the old snapshot in the boot menu.

Its hard to break ZFS.

---

### Post by SunnyRabbiera on 2009-11-23
EXT3 is more then fine for me, i tried the others like XFS, reiser and JFS but none of them are as supported or as smooth as EXT3

---

### Post by Rainstride on 2009-11-23
> **lightningfox said:**
> Hello

I want to know what's the best file system for using Linux as a desktop
operating system.

Right now I use ext3 for all my partitions.

I want to know what other people use and which filesystem they think is
best.

Im using ext4 on all my drives, its got great performance all around. you can pretty much use it in almost any case, whether it be a setup with tons of tiny files or a hand full of huge ones. I know there's one or two that specialize in solid state drives.  as for the supposed "data corruption" I don't think it has anything to do with ext4, I have a 20gb encrypted file that I had to move when I redid the partition on my external and i moved it back and forth 2 times between two ext4 partitions, so its a very stable filesystem. and there was no corruption witch would have been obvious the moment I decrypted it.

---

### Post by jowilkin on 2009-11-23
> **blueshiftoverwatch said:**
> JFS and XFS are mainly for dealing with large files and /home is generally just a whole bunch of very small files for storing settings.

/home is generally for all your data which should include a LOT more than just some settings files.  There should definately be a lot of small .config files in there, but there should be lots of other stuff too...

For the OP, I have had luck with ext4; no corruption issues or anything like that.  I think it should be adopted over ext3 for most home users as long as you have a backup (which you should have anyway).  If you absolutely cannot lose data, then stick with ext3, it's been tested and tweaked for many years.

I like ZFS, but the only implementations on linux are FUSE (userland, not kernel based) so I would not use it on linux.  btrfs is supposed to bring many of the nice features of zfs to linux users, but it is not ready yet for regular use.

I also like XFS, but I don't see a compelling reason for an average desktop user to choose it over ext3/4.  It does not seem to be as actively maintained and I would question its stability compared to ext3/4.  That being said, I do use it for my home partition on one machine :)

---

### Post by jowilkin on 2009-11-23
> **Rainstride said:**
> Im using ext4 on all my drives, its got great performance all around. you can pretty much use it in almost any case, whether it be a setup with tons of tiny files or a hand full of huge ones. I know there's one or two that specialize in solid state drives.  as for the supposed "data corruption" I don't think it has anything to do with ext4, I have a 20gb encrypted file that I had to move when I redid the partition on my external and i moved it back and forth 2 times between two ext4 partitions, so its a very stable filesystem. and there was no corruption witch would have been obvious the moment I decrypted it.

The corruption has to do with the fact that ext4 does not commit file changes to disk as quickly as ext3.  This causes speed advantages, but many programs were written expecting data to be written to disk as fast as ext3, not expecting the long delay in a filesystem like ext4.  This is not a bug, it is a perfectly legitimate filesystem design.

So you would not see the corruption under normal circumstances, it would be when you have a sudden crash or loss of power.  That said, I believe the developers have made a few changes to ext4 to mitigate this problem.  Personally I've had a few crashes and never lost any data.  But it was a real problem with ext4.

---

### Post by Rainstride on 2009-11-23
> **jowilkin said:**
> The corruption has to do with the fact that ext4 does not commit file changes to disk as quickly as ext3.  This causes speed advantages, but many programs were written expecting data to be written to disk as fast as ext3, not expecting the long delay in a filesystem like ext4.  This is not a bug, it is a perfectly legitimate filesystem design.

So you would not see the corruption under normal circumstances, it would be when you have a sudden crash or loss of power.  That said, I believe the developers have made a few changes to ext4 to mitigate this problem.  Personally I've had a few crashes and never lost any data.  But it was a real problem with ext4.

If your talking about the one everyone was have trouble with when testing ext4 in jaunty, then that was fix about 4 months back. im talking about the one that was in the release notes for karmic. though if you read the bug report, they have pretty much no data on it or whether its ext4 or some program incorrectly handling data in certain instances.

---

### Post by running_rabbit07 on 2009-11-23
I use EXT4 for every partition and have had zero problems with it.

---

### Post by Sealbhach on 2009-11-23
> **running_rabbit07 said:**
> I use EXT4 for every partition and have had zero problems with it.

Me too. And I found it was much much faster than EXT3, definitely worth going to the trouble of formatting to it.

.

---

### Post by jowilkin on 2009-11-23
> **Rainstride said:**
> If your talking about the one everyone was have trouble with when testing ext4 in jaunty, then that was fix about 4 months back. im talking about the one that was in the release notes for karmic. though if you read the bug report, they have pretty much no data on it or whether its ext4 or some program incorrectly handling data in certain instances.
Yes, I was talking about the problems people were having with all distros with delayed allocation when ext4 was first introduced.

I see that the release notes do mention a bug related to large files with ext4 ([here]("http://www.ubuntu.com/getubuntu/releasenotes/910#Possible%20corruption%20of%20large%20files%20with%20ext4%20filesystem")). There are a few other bugs that people have run into with ext4, but they all seem to be pretty rare so I wouldnt really worry about them, especially if make regular backups.

---

### Post by autocrosser on 2009-11-27
I've been using EXT4 from the very early testing days & have only had major crash/data loss within the first couple of months of its release...which would be expected. I started using it in late 2008 (October) & have had 0 problems with the shipped version for Karmic...that with crashes from Gnome-Shell (for the last 8 months) & then regular testing work with the Lucid startup, so I would say that EXT4 is more than stable enough for daily use...there are still a couple of corner-case bugs, but they don't bite very often & EXT3 to this day also had a couple of corner-case ones too....

---

### Post by gnomeuser on 2009-11-27
I am using btrfs, it is treating me very well. Though to be deemed stable for production much more testing will be needed. Regardless this will be your filesystem of choice within a year or so, right now go with ext4. The upgrade to btrfs come time will be smooth and can be reversed if needed.

---

### Post by SKLP on 2009-11-28
I'd say ext4 for now. Probably btrfs in a while...

---

### Post by NightwishFan on 2009-11-28
I would advise ext3 if you do not really understand the benefits or downsides. If you want something a little newer, try ext4.

Nothing wrong with trying reiserfs or xfs, though please note once you have data on a drive, it is hard to move it all around to convert back.

---

### Post by cascade9 on 2009-11-28
> **KiraLexi said:**
> ZFS is nice if you have a distribution that supports it. I remember doing something unspeakably stupid to a Solaris installation once, rebooting... and just selecting the old snapshot in the boot menu.

Its hard to break ZFS.

I'm pretty sure that eventually btrfs wil have all, or almost all, the features of ZFS, with none of that stuffing around with FUSE to get it going on Linux. 

> **gnomeuser said:**
> I am using btrfs, it is treating me very well. Though to be deemed stable for production much more testing will be needed. Regardless this will be your filesystem of choice within a year or so, right now go with ext4. The upgrade to btrfs come time will be smooth and can be reversed if needed.

I'm hoping to move to btrfs at some point in the future. When it get to a stable version. It seems like it will be a very good file system from all I've read and heard about. 

For the moment, though, I'm sticking with EXT3. Its old, but very stable. If I have to get a new hdd before btrfs gets to a stable release, I might move to EXT4.  

BTW, I was pretty impressed when I found this- 

[http://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3](http://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3)

Not sure if its something I would do.....not without backing up my data anyway. But neat feature :)

---

