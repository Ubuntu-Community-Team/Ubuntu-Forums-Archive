---
title: "EXT3, XFS, JFS, ReiserFS - which file system is best?"
date: 2007-06-14
forum: The Cafe
---

### Post by james_2002uk on 2007-06-14
I've been reading a bit about different file systems (what with Linus and Schwatz and ZFS being mentioned allot).

Ubuntu defaults to ext3 but has anyone given XFS, JFS or ReiserFS a go? I've seen some benchmarks and they are said to be properly fast but I was wondering if there are any down sides (otherwise presumably linux would default to one of them instead) with stability etc?

---

### Post by LightB on 2007-06-14
I prefer jfs, but ext3 is more tried and tested. and things like selinux work with it.

---

### Post by Aranel on 2007-06-14
Anyone, feel free to correct me on any of this. I'm combining personal experience with what I've read before, so...

Ext3 is *the* Linux filesystem; it's guaranteed to be recognized by any Linux system, and it's got the biggest support base. That's probably why it's Ubuntu's default; there's really nothing special about it as far as performance goes (although that isn't to say it's a bad filesystem--far from it).

Reiserfs is generally accepted to be the fastest in dealing with small files, which makes it very effective for personal use. It also deletes stuff with indecent speed. If you want a ready-to-go and very fast filesystem, I'd recommend going with reiserfs.

JFS is pretty much well-rounded. It's what I currently use, and I can't complain about it. :)

XFS is very efficient in handling large files, and with [some small tweaks](http://everything2.com/index.pl?node_id=1479435), its performance in other areas rivals that of other filesystems. By design, it's very secure, but some consider this a potential downside. For example, in an extremely rare occurrence, when a file is written by copying over another file, a poorly-timed crash/power outage results in the file being written with nonsense (to protect potentially sensitive data). But again, this is extremely unlikely to happen, and XFS is one of the oldest and most well-established filesystems available.

None of them have any stability problems or anything. At the very least, they all beat the pants off NTFS and HFS+.

I hope that helped some!

---

### Post by starcraft.man on 2007-06-14
I just stick with Ext3, its served me well by being reliable, well supported and problem free it seems (I don't care much about speed...). I've read up on the others but I can't seem to find that much incentive to change to any of them. I'm gonna stick with what works, might mess around with it on my new computer when it gets here just for fun and to see actual differences.

---

### Post by Omnios on 2007-06-14
Counts on you available disk space as I heard that  Reiserfs uses disk space better so on a small disk drive or on a system where available disk space it might be better. Then again if you have 200 gig it might not matter.

---

### Post by hanzomon4 on 2007-06-14
I'm using jfs for / and xfs for /home, I can't really complain. The one problem I have is that you can't resize these file systems so I have to use a usb hard drive for testing other OS's. I heard the same as Aranel so nothing really to add. 

What about UFS and ZFS anyone have any experience with these filesystems? I used UFS with pc-bsd but I'm not to deep in exploiting advanced features and such.

---

### Post by tehkain on 2007-06-14
WAFL from netapp(not OnTap with WAFL since that mean a crappy OS with a good system)

I want to see some WAFL on linux to ZFS on OSolaris comparisons.

---

### Post by starcraft.man on 2007-06-14
I was reading up on [ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS") just now cuz I'm probably gonna try that next time I reinstall and I came across this in the Wiki article, can someone explain what it means to me... I didn't get it, I'm not super read up on these things though.

[QUOTE=Wikipedia]Some directory operations (including unlink(2)) are not synchronous on ReiserFS, which can result in data corruption with applications relying heavily on file-based locks (such as mail transfer agents qmail[3] and Postfix[4]) if the machine halts before it has synchronized the disk.[5][/QUOTE]

---

### Post by diesel1 on 2007-06-14
Hi,

I always use Reiserfs for / and /home, it is very good at recovering from crashes and if there are certain issues with the journalling you can read the file system as ext3.

I tried xfs but have never had satisfactory results.

Diesel1.

---

### Post by james_2002uk on 2007-06-14
Thanks!... I think i'll have an experiment. I've also heard that xfs boots up a bit quicker so I think i'll try using XFS on / - not sure what to use on /home - lots of small and large files!

---

### Post by NeoLithium on 2007-06-14
I have XFS through and through for all of my partitions and it works just fine for me :)

---

### Post by Anthem on 2007-06-14
I always use the default for a given distro, which means I'm using ext3 right now.  But I've got nothing but good things to say about Reiser... it's twice saved my data during a full hard drive crash.

XFS isn't something you'd generally use on a personal computer, nor is JFS.

You can pretty much stick to Reiser and ext3 and be fine.  Reiser might be depreciated, though, since Hans is in jail.  The next-gen filesystems are Reiser4 and ext4.

---

### Post by luca_linux on 2007-06-15
Technically (and I'd say also actually) ZFS is the best file system out there.
Yet there's still no port on Linux, mainly due to (stupid) license issues.
Among the ones available for Linux, I think the best is JFS, it's fast and reliable. Never had a problem with it.
Ext3 is very stable and all, but it is slow.
XFS is very good, but I think JFS is still superior, especially for its reliability.
I've heard of many people complaining about ReiserFS, not to say about Reiser4.

So: JFS.

---

### Post by theseeker on 2007-06-25
To contribute to the discussion:

[Filesystems (ext3, reiser, xfs, jfs) comparison on Debian Etch]("http://www.debian-administration.org/articles/388")

There are reports though that XFS has caused severe data loss after system crashes.

---

### Post by mips on 2007-06-25
I use XFS.

---

### Post by Lostincyberspace on 2007-12-31
I see EXT4 is out is it any good?

---

### Post by insane_alien on 2007-12-31
ext3is a good all rounder. to be honest, if you need to ask the question 'which filesystem is the best' you really don't need another filesystem. 

ext4 is out, but the ubuntu version of the kernel doesn't support it. i have an ext4 partition on my arch laptop and it appears stable but i haven't really done anything extensive with it. when it is stable the ubuntu devs will toggle the little switch in their kernel configs(it really is just a y/n option in the configuration) and compile the kernel with ext4 support. personally, i would like it if the kernel had it enabled just so if those who knew what they were doing could make an ext4 filesystem and muck about with it.

---

### Post by jeffus_il on 2007-12-31
Here's an easy comparison of the popular file systems on Debian:

[http://www.debian-administration.org/articles/388]("http://www.debian-administration.org/articles/388")

---

### Post by kellemes on 2007-12-31
> **Anthem said:**
> But I've got nothing but good things to say about Reiser... it's twice saved my data during a full hard drive crash.
(..)
You can pretty much stick to Reiser and ext3 and be fine.  Reiser might be depreciated, though, since Hans is in jail.  The next-gen filesystems are Reiser4 and ext4.


I'm not afraid Reiser will die, it's not depending on Hans alone.
I always use Reiser for /var .. depending on the distro I'm using.
Only downside seems to be the mount-time, but heck..

Anyway, these filesystems all have there pro's and cons, you could use 3 different filesytems for 3 different partitions if you're going for the best of performance or safety, like..
/boot    - ext2
/           - ext3
/home  - ext3
/var      - reiserfs

Most of us probably won't notice any difference though.. :popcorn:

---

### Post by insane_alien on 2007-12-31
> Most of us probably won't notice any difference though

this is true. you don't start noticing differences until you start approaching the limits of one filesystem or more. 

for instance, a 2TB ext3 partition performs horribly compared with a 2 TB XFS partition and it is very noticable(3 minutes to mount versus nearly instantly) 

i want ZFS for linux but until solaris either port it themselves or reliscence it won't happen.

---

### Post by FuturePilot on 2007-12-31
I've never experimented with other file systems but EXT3 is just fine for me.

---

### Post by AusIV4 on 2007-12-31
One warning about XFS and JFS is that they can't be reduced. I always separate root and home file systems so I can re-install the OS without losing my /home data. 

On my laptop, I resize fairly often, so I use ext3 for both root and /home. 

On my desktop, I have a 40 GB drive that has two different root file systems on it (one stable, one experimental) and a couple GB swap. Then I have a 500 GB RAID-5 (offers redundance) with an LVM layer on top that is formatted as JFS. I put the LVM layer on top so when I get a couple more drives (probably 2x500GB) I can RAID them together and expand my logical volume without having to rebuild my entire array.

Generally, I recommend ext3 if you think there's any chance you'll want to resize your partitions, otherwise I'd use JFS for performance and stability.

---

### Post by articpenguin on 2008-01-06
ive used JFS on opensuse. yes JFS is a little faster than ext3 its really not noticable. JFS is a filesystem that is maintained by 1 person and not supported by a couple of distros including Opensuse. forgot the other 2 distros i think slackware and fedora

---

### Post by yatt on 2008-01-06
My $0.02

Ext3 - The only FS of the bunch readable by Windows. IME, it is the best at handling power outages and other anomalies. It is rather slow. For most file operations you won't notice, but it takes a long time to mount. This will cause a noticeably longer boot time. To make it worse, every X mountings, it has to go through its log which can take longer still. However, it is still the best in stability and support which is why nearly every distro uses it.

ReiserFS - ReiserFS is great with lots of small files. It can also delete quickly. It is a good choice for /var. It takes nearly as long as Ext3 to mount, but it does not have to replay its journal. It was a popular default FS for distros, but most have switched to Ext3 due to upgrading concerns (the Ext4 devs are guarenteeing that your Ext3 partition can be upgraded without any issues).

JFS - Tends to be the lightest on system resources. It tends to offer good performance everywhere, while not standing out in any category. It mounts quickly and is acceptable with power-failures/etc. It lacks support and high levels of usage which has really prevented any distro from making it the default. I use it for my /.

XFS - The fastest FS in the group, particularly with big files. It also scales nicely. It was designed for workstations the deal with thousands of large files, and it does that role well. In the desktop world, some of its features become faults. It does not handle power outages well. You should expect at least one file to be a string of garbage, when you do get the machine running again (if it is your /). If you use it on a partition that does not get written to often, it should be fine.  I use XFS for a partition I use to store my music. 

Ext2 - People still like to use it for /boot. Ext2 does not have a journal, so it can lose data if something goes bad. However, /boot rarely changes. Upgrading your kernel (due to how most package managers handle it), tends to leave very little room for catastrophic error due to your /boot FS.

---

### Post by Erunno on 2008-01-06
XFS due to its fragmentation-preventing technologies like being extent-based and using delayed allocation. It also has an online defragmentation tool in case the fragmentation surpasses an acceptable level which will eventually happen to any filesystem which is constantly written to. Reportedly its also good at handling extented attributes which are kept with the inode if you reserved enough space (and in b-trees otherwise) and the overall read/write performance is usually comparable to ext3 at worst.

For the longest time the standard mkfs options where suboptimal and it was recommended to format a partition manually since SGI used some very conservative options to keep backwards compatibility. Unfortunately this also meant that new XFS developments like version 2 journals, lazy-count and attr2 where not used. From what I've this situation has improved with the most recent release of xfs_progs though.

Since XFS also features out-of-order writes of metadata and data its prone to cripple data in case of a power outage or complete hardware failure but I've never encountered such problems on my laptop which comes with a UPS by default and I'm very conservative when it comes to third-party packages so my systems are ususally very stable.

---

### Post by x0as on 2008-01-06
> **yatt said:**
> 
The current version of Grub cannot boot from a XFS file system. If you want to use XFS as /, you have to make a separate /boot. I use XFS for a partition I use to store my music. 


That's news to me, my root partition is xfs and grub boots it fine.  I've got no separate boot partition.

> In the desktop world, some of its features become faults. It does not handle power outages well. You should expect at least one file to be a string of garbage, when you do get the machine running again (if it is your /)

I've had no problems with corruption despite a couple of power cuts recently.

---

### Post by Erunno on 2008-01-06
> **yatt said:**
> The current version of Grub cannot boot from a XFS file system. If you want to use XFS as /, you have to make a separate /boot.

GRUB can boot from XFS partitions since version 0.91.

---

### Post by yatt on 2008-01-06
> **Erunno said:**
> GRUB can boot from XFS partitions since version 0.91.
News to me. I actually haven't used XFS as / for about a year or so. Back then, it was an issue.

---

### Post by yatt on 2008-01-06
> **x0as said:**
> That's news to me, my root partition is xfs and grub boots it fine.  I've got no separate boot partition. Apparently the issue has been dealt with. Grub used to not be able to boot from it.

> I've had no problems with corruption despite a couple of power cuts recently.I did. Lots. So have many other people. I have lots my xorg.conf a few times, and had my ~/.kde directory thoroughly thrashed. XFS buffers delay in memory to increase performance and reduce fragmentation. If the power goes out before that write actually occurs, you could run into a few issues. The most common are to have an old version of a file, and to have a file reduced into a string of 0s. The chance of data corruption increase if you write allot before the outage (ie run synaptic and update a few dozen packages).

---

### Post by Blutack on 2008-01-06
> Ext3 - The only FS of the bunch readable by Windows. IME, it is the best at handling power outages and other anomalies. It is rather slow. For most file operations you won't notice, but it takes a long time to mount. This will cause a noticeably longer boot time. To make it worse, every X mountings, it has to go through its log which can take longer still. However, it is still the best in stability and support which is why nearly every distro uses it.

Longer mount times?  I have always used ReiserFS until my last reinstall, where I bare installed with both.  EXT3 seemed to damn near halve my boot time.  General usage seems same.

---

### Post by reacocard on 2008-01-06
> **Blutack said:**
> Longer mount times?  I have always used ReiserFS until my last reinstall, where I bare installed with both.  EXT3 seemed to damn near halve my boot time.  General usage seems same.

I have had a similar experience. I tried reiser once because I had heard it was faster, but my startup time increased by 10-15 seconds! That means reiser is taking about 5 seconds longer than ext3 to mount (as I had several partitions).  I found that unacceptable so I went back to ext3 which I am still happily using.  I would try XFS except for the fact that my tinkering tends to make my computer crash a lot and from everything I've heard that's what XFS deals with the worst. ext4 looks promising though, can't wait for it!

---

### Post by toupeiro on 2008-01-06
> **tehkain said:**
> WAFL from netapp(not OnTap with WAFL since that mean a crappy OS with a good system)

I want to see some WAFL on linux to ZFS on OSolaris comparisons.

I believe you have to license WAFL, don't you?  I have three netapp filers I support at my local site and I recall Network Appliance being very critical of what you use a netapp head on. (Very robust and fast, but not as openly available.  Like Veritas FS for SAN storage which you have to license?)
The benefit to ZFS then would be its free availability and indifference to varying types of disks.  WAFL gets very fussy, for example, if you create an aggregate with Fiber Channel and SATA/SAS disks together.  For performance, no clue how ZFS and WAFL compare.

---

### Post by SunnyRabbiera on 2008-01-06
> **yatt said:**
> My $0.02

Ext3 - The only FS of the bunch readable by Windows. IME, it is the best at handling power outages and other anomalies. It is rather slow. For most file operations you won't notice, but it takes a long time to mount. This will cause a noticeably longer boot time. To make it worse, every X mountings, it has to go through its log which can take longer still. However, it is still the best in stability and support which is why nearly every distro uses it.

actually Ext3 is pretty quick sometimes, depending on the distro.
Ubuntu and mandriva are really speedy with it

---

### Post by yatt on 2008-01-06
> **SunnyRabbiera said:**
> actually Ext3 is pretty quick sometimes, depending on the distro.
Ubuntu and mandriva are really speedy with it
Hmm, I haven't used Ext3 in a good while. Back then, Ext3 and Reiser where quite comparable. I think my starttime with Ext3 or Reiser was ~1:15 and there was only a second or two difference between the two. At the time, XFS got it down to ~45.

---

### Post by new2*buntu on 2008-01-06
I use Reiser for my /media/Documents (where I put everything) and ext3 for /. I just don't really like the huge "lost + found" folder on ext3, since my HD isn't huge (80GB).

---

### Post by jfdill_2 on 2008-01-08
I use a fixed-size ext3 for "/" (actually 2 root partitions, production and backup)
I use reiserfs over LVs for directory trees that I split off from "/"
I am revisiting using JFS or XFS, and evaluating cluster filesystems

I periodically copy the production root to the backup root, especially before major upgrades.  That way, if anything goes wrong, in a few minutes I can boot off a Live CD and set up the system to boot off the backup root, much faster than trying to restore from backups.  This really works great for distribution upgrades, since you can always reboot to the old version if there are major problems.

Some people have complained this is a waste of disk space, but this method has saved me on more than one occasion, after all disk space is cheap nowadays.  If the disks are too small, I will set up small /boot as ext2 or ext3, and use LVs for root and backup root.

ext3 for root is nice since it is usually in the stock kernel, in some cases I will not need an initrd to boot, and it can be easier to use a Live CD to recover.

Reiser, JFS and XFS can be extended on the fly, which works great with LVM.  That way, I can use the same basic partition strategy for multiple purposes, and split off and grow directory trees depending on how the system is actually used.  For example /usr/share can usually be split off from / easily to free up space if needed, though if you split off /usr/lib you can get into trouble if it is not accessible during boot.  I will also split off directory trees that I want to be persistent across distribution upgrades like /home, /var/www.  To be safe, I may not even mount them during the upgrade, then integrate after.

XFS' killer app is xfsdump / xfsrestore, which are wonderful utilities, use surprisingly less resources than GNU tar for example.  However, since I have abandoned tape and backup to disks instead (BackupPC with rsync) this has become less important, and I am not sure if I trust XFS 100% due to the potential corruption issues.

I had some serious problems with ext dump / restore several years ago and have not been tempted to try it again, whether or not that is any longer justified.

---

### Post by mips on 2008-01-09
For kubuntu I was using Ext3 on a LVM but I wiped kbuntu and plan on installing Arch but I'm not sure what filesystem I want to use on the LVM this time around. I 'm thinking about ext3 for stability and utils but then again I like XFS for it's faster mounting times and overall performance.

What should I do?

---

### Post by Xbehave on 2008-01-09
what sort of crash kills an xfs partition? i remember loosing a whole install when something shorted in my desktop,
If im using a laptop am i safe? Does JFS have the same 'flaw'
has anybody used reiser4? is it possible in ubuntu?arch?
why arent theyre any rouge kernel devs who dont care about licenses and have made a zfs patch :(

---

### Post by Ubuntist on 2008-01-09
I used to use Reiser and had no problems with it.

Then I switched to ext3, because the utilities for full read/write access between Ubuntu and XP require it. It's worked just fine for me, and I can't say I've noticed the difference in performance. But then I'm not what you would call a power user.

---

### Post by aeto on 2008-01-09
JFS for laptops, XFS for servers, ReiserFS for multimedia desktops, EXT3 for workstations.

I've been a JFS user for more than a year, mostly because I remember having read about it being low-latency (alongside EXT3) and that suited my DAW requirements. Furthermore, low power consumption is another factor to consider for my portable machines. Only my /boot partitions have remained EXT3. Stupid me, it is senseless to have a journalled boot but oh well.

Contrary to popular myth, EXT3 is a superb FS. It's a good compromise, sort of an all-around performer. So is JFS. Ja, ZFS is gut, but there are technical barriers and limitations. If they coulda done it, they woulda, as noted - [http://en.wikipedia.org/wiki/ZFS#Linux](http://en.wikipedia.org/wiki/ZFS#Linux)

And uhh..if your FS seems to fail you, like lose data, crash, whatever, it's really just YOU who have failed :) Unless of course you gave in to alpha stuff like EXT4 and Reiser4.

---

### Post by bcr88 on 2008-03-07
I've always used ext3 (and sometimes ext2 on certain partitions) since I started using Ubuntu last winter.

However, I usually manage to mess up my install and have to reinstall it every once and a while. Now would be one of those times...

So, this time I wanted to try a different filesystem or two. I'm going to create a /, /boot, and /home partition. 

From what I've read so far (which was anything but conclusive), ReiserFS is supposed to be good with small files and small partitions, so I was going to use that for my /boot.

I was going to use ext3 for /home since if I should ever want to read it from OS X I should be able to by installing a program.

I was also thinking about using XFS for / because it's supposed to be fairly quick, and one thing I read said it somehow takes advantage of multiprocessor computers. I'm on a laptop, so power loss is not a concern as far as corrupting files.

Does this sound like a reasonable idea? If anyone has any comments or suggestions, they would be appreciated.

---

### Post by LightB on 2008-03-07
bcr88, I found jfs to be overall faster than xfs. I hear xfs is supposed to be faster with large files. In a PC, how often does one deal with large files compared to small ones?

I notice I commented on this thread before. Here is an update, use jfs carefully. I implied that before, but now I emphasize. I've since seen the pitfalls of jfs - it was probably bad hardware, either way, jfs not as resistant against screw ups as ext3, it seems.

---

### Post by sloggerkhan on 2008-03-08
I use combos of ext3, jfs and xfs. I heard that some of the advantages designed into xfs for work with the distributed multi-machine applications it was designed for also scale to multiple cores. Not sure how true that is, but I'm currently using it on my storage partition, which is mostly graphics and videos. I'd never heard about the problems with it from power outages, though. In general, I've always thought ext3 doesn't seem quite as fast and corruption resistant as I'd like. I've had good experiences with jfs, though.

Haven't used reiser.

---

### Post by SunnyRabbiera on 2008-03-08
I favor Ext3 and XFS, both have served me well

---

### Post by macogw on 2008-03-08
Here, I did a [5 page paper on file systems](http://colbyframeco.com/~maco/nix/fs.pdf) for my system administration class.  I thought XFS sounded extremely cool, but I emailed a [friend who is a file systems expert](http://valhenson.org) and asked what she thought.  She said > My recommendation on which file sysytem to use goes like this:

1. Use ext3...
2. Unless it doesn't perform well enough, in which case use XFS.

You should use ext3.

---

### Post by bcr88 on 2008-03-08
Yeah, I know Ext3 is the most common and recommended, but I just feel like doing a little experimenting. Either way, I think I'll use Ext3 for my /home partition. I'll take a look at your paper though

P.S. You're from Pittsburgh? Me too.

---

### Post by Rhapsody on 2008-03-08
I've used ext3 all the time I've been using Linux. It was a bit sketchy on my old system (which was unreliable anyway) but has performed well on a newer system. I'll probably keep going with it and upgrade to ext4 once it's stable enough.

---

### Post by jrusso2 on 2008-03-08
> **macogw said:**
> Here, I did a [5 page paper on file systems](http://colbyframeco.com/~maco/nix/fs.pdf) for my system administration class.  I thought XFS sounded extremely cool, but I emailed a [friend who is a file systems expert](http://valhenson.org) and asked what she thought.  She said

I don't agree with your expert. IMO Ext 3 is the least stable and should be avoided if possible.

This is the only file system in Linux where I have ever lost data and if you search the forums its always the one that people have lost data or it won't mount or fsck is messed up.

Linus has been agonizing about finding a replacement for ext 3 because of fsck.  Can you imagine rebooting a server with terrabytes of data and having to wait for FSCK to run it could take all day.

---

### Post by bonzodog on 2008-03-08
I have always used ReiserFS myself, it's very fast, and has been 100% reliable for me. I have even been able to rebuild the tree on my /home (which has never been re-formatted, due to large amounts of data in there) without any data loss.
It's definitely better for use with the typical home user, who doesn't have too many files above 1GB hanging around on the disk, and yes, it's indecently fast at deletion.

---

### Post by articpenguin on 2008-03-08
"ext3 sucks in many ways. It has huge inodes that 
take up way too much space in memory. It has absolutely disgusting code to 
handle directory reading and writing conditional indexing code is horrible. Its performance absolutely sucks 
when the journal is being drained or something."

[http://lkml.org/lkml/2006/6/9/183](http://lkml.org/lkml/2006/6/9/183)

---

### Post by yatt on 2008-03-08
What I think will be interesting is solid state hard drives. While the current list of filesystems will all work fine, they just won't be anywhere near as fast as the could be.

---

### Post by macogw on 2008-03-09
> **jrusso2 said:**
> I don't agree with your expert. IMO Ext 3 is the least stable and should be avoided if possible.

This is the only file system in Linux where I have ever lost data and if you search the forums its always the one that people have lost data or it won't mount or fsck is messed up.

Linus has been agonizing about finding a replacement for ext 3 because of fsck.  Can you imagine rebooting a server with terrabytes of data and having to wait for FSCK to run it could take all day.

Ext3 can be made to do writeback-only journalling, like XFS does, but that's supposed to have a higher risk of data loss.  The thing about ext3 when it comes to "undeleting" is that it clears the inode when you delete a file so there's no longer a pointer to the file.  Ext2 doesn't.

---

### Post by articpenguin on 2008-03-09
I to had courrption with ext3 and ran into several of its drawbacks.

1.Ext3 once formatted had 1400Mb of overhead on a 132Gb hdd not including the reserved 5%.

2. EXT3 does not support more than 32k sub-folders which i run into with flightgear.

3. directory looks ups are real slow even with htrees.

4. Ext3 is a pig with inodes.


I currently use JFS .

---

### Post by sonnet on 2008-03-19
on this article:
[http://linuxhelp.150m.com/resources/fs-benchmarks.htm](http://linuxhelp.150m.com/resources/fs-benchmarks.htm)
it seems that mounting reiser4 will make you gain 15% of space disk,because of transparent compression.
That's amazing!
Does anyone know if it's true?
The only drawback according to the article is that with newer kernel reiser4 is getting worse performance because the kernel's developer want sabotage this filesystem (though it's not included in the main branch )

---

### Post by Washer on 2008-03-19
yeah reiser4 is pretty badass. I was getting much faster copy times onto an external disk. Problem is you have to patch your kernel, or get one that's already patched.

I'll run a few benchmarks later if anyone's interested.

---

### Post by Washer on 2008-03-19
I just did a test right now using bonnie++ (it's in the repos)

ext3
```
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ubuntuuser-pc    4G 51541  68 53685  14 25609   4 51093  55 53825   2 119.0   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++


```

reiser4 /w gzip compression
```
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ubuntuuser-pc    4G 83241  94 168469  28 196880  70 72470  91 402477  87  1115   8
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ 27687 100 30303  94 +++++ +++ 31493  99
```

make your own conclusions

---

### Post by sonnet on 2008-03-28
> **Washer said:**
> I just did a test right now using bonnie++ (it's in the repos)

ext3
```
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ubuntuuser-pc    4G 51541  68 53685  14 25609   4 51093  55 53825   2 119.0   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++


```

reiser4 /w gzip compression
```
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ubuntuuser-pc    4G 83241  94 168469  28 196880  70 72470  91 402477  87  1115   8
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ 27687 100 30303  94 +++++ +++ 31493  99
```

make your own conclusions

Really thanks for the benchmarks, but speed over 150mb/s are not too high to be true?
I read somewhere that some filesystem give fake results because it's like they consider finished a job (because they heavily usa the cache ) when it's really not.

---

### Post by djbsteart1 on 2008-03-28
what about BTFS, its surely got something in Linux's future, its till in beta, but it already is up with XFS and is far faster then JFS. It also seems to be able to support many of the ideas that are in ZFS.
A small comment about Reiser, by this I mean Hans Reiser, the man who created it, he has more than once sad that the Linux kernel is crap and the only code in it worth useing is his own. Now whither this is true about the code or not doesn't bother me. I will not use a filesystem designed by someone who says something like that, no matter if it is better or not.

---

### Post by reacocard on 2008-03-28
> **sonnet said:**
> Really thanks for the benchmarks, but speed over 150mb/s are not too high to be true?
I read somewhere that some filesystem give fake results because it's like they consider finished a job (because they heavily usa the cache ) when it's really not.

probably the data bonnie++ uses is highly compressible and thus gets a bigger benefit from the compression than most data would. I'd be more interested in seeing performance using, say, a video file.

---

### Post by rumli on 2008-03-31
I've used ext3, jfs, and reiserfs in the past.  Ext3 was okay but generally slow, and the occasional filesystem check on boot was a pain in the neck and essentially a deal-breaker for me.  ReiserFS was very fast, although it takes noticeably longer than Ext3 to mount upon boot.  On the other hand, it never unpleasantly surprises me with a full filesystem check like Ext3 does.  I used ReiserFS on a physically bad drive, and it withstood quite a few bad sectors for quite a while (months) before it finally failed completely.  JFS was fast, but it screwed up really badly and I lost the entire contents of the partition when the computer completely froze and I had to reboot using the power switch.  It will be a long time before I try JFS again.

---

### Post by D-EJ915 on 2008-03-31
most of my drives are JFS and they've survived 4 or 5 power failures with no problems, 2 of them right after one another too, guess it depends on what's going on.

---

### Post by el mariachi on 2008-04-01
I never used anything else than Ext3. 
I've been thinking about something though... I own a Maxtor external hdd, which is formated in NTFS. Is there a way to use an open source FileSystem in these types of hdd's? or will it most likely fail do work?

---

### Post by SupaSonic on 2008-04-01
I use ReiserFS for / and ext3 for home. I would've used reiserFs for /home also, but I don't have an external hdd to dump the files. Anyway, ext3 had caused kernel panic situation after power failures on 2 occasions for me, so I doubt I'll ever use it again for /.

---

### Post by anaconda on 2008-04-01
> **el mariachi said:**
> I never used anything else than Ext3. 
I've been thinking about something though... I own a Maxtor external hdd, which is formated in NTFS. Is there a way to use an open source FileSystem in these types of hdd's? or will it most likely fail do work?

Yes. you can format external USB hdd:S to whatever fs you want.

So it will work, but all data that you have on those NTFS partitions will be lost when you format..

---

### Post by djbsteart1 on 2008-04-01
> **el mariachi said:**
> I never used anything else than Ext3. 
I've been thinking about something though... I own a Maxtor external hdd, which is formated in NTFS. Is there a way to use an open source FileSystem in these types of hdd's? or will it most likely fail do work?

Also if you change from NTFS to a Linux FS, Windows computers wont be able to read the drive, whither that an issue or not I don't know, but its worth thinking about.

---

### Post by articpenguin on 2008-04-01
windoze can read ext2/3.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by BOBSONATOR on 2008-04-01
I want Reiser4 so bad, but i dont want to delete my partition lol.

I will probably do it one day when it creeps up on me

---

### Post by el mariachi on 2008-04-02
My ext3 partition died on me again today...I never lose any data, it's just the journal that gets messed up. the Kernel panics.
 
as simple check fixes it... I really need to try another FS but I don't know which. humm

---

### Post by Loranga on 2008-05-06
How do I do to run Reiser4 partititons in 8.04? Initially for non-root ("/") partitions, but later on even for partitions mounted on "/". Thanks in advance!

---

### Post by aamukahvi on 2008-05-06
jfs /
ext3 /home

---

### Post by insane_alien on 2008-05-06
> **el mariachi said:**
> My ext3 partition died on me again today...I never lose any data, it's just the journal that gets messed up. the Kernel panics.
 
as simple check fixes it... I really need to try another FS but I don't know which. humm

are you sure your drive is functioning correctly?

the last time that happened to me was because of a disk going bad. lasted a week after i started getting them although it technically still worked at the end as you could still get some data off it, though mostly incomplete and corrupted.

---

### Post by Twitch6000 on 2008-05-06
I heared JFS is like the second fasted to use on ubuntu so yeah.I just use EXT3 though.

---

### Post by el mariachi on 2008-05-06
> **insane_alien said:**
> are you sure your drive is functioning correctly?

the last time that happened to me was because of a disk going bad. lasted a week after i started getting them although it technically still worked at the end as you could still get some data off it, though mostly incomplete and corrupted.
SMART says everything is great with the hd's... so far XFS hasn't been trouble

---

### Post by blithen on 2008-05-06
I use ReiserFS for my home partition. EXT3 for my / partition. I love ReiserFS. just haven't changed over the / partition yet.

---

### Post by Half-Left on 2008-05-06
Recently switch to Reiserfs with hardly 64bit, it's just faster, I can tell the difference from ext3. Only the mount time is longer but after that it blazers along.

---

### Post by zappa86 on 2008-06-03
I want Reiser4 really bad as well. But, to have it, someone will need to break Hans out of jail. Any takers? You'll get a sweet FS out of it...

---

### Post by billgoldberg on 2008-06-03
I use reiserfs and am happy with it.

---

### Post by Luke has no name on 2008-06-03
An Ubuntu admin book I picked up recommended using ext2 for /boot, as using a journaling FS on a (what they recommend to be) 100MB partition is wasteful.

I know very little about filesystems, but I do use ReiserFS at the moment, since I hear bad things about ext3 and RFS can do things more easily than JFS, such as resize partitions and read from Windows.

ZFS sounds badass, the FS of the future, if they had it for Linux native (stupid CDDL).

---

