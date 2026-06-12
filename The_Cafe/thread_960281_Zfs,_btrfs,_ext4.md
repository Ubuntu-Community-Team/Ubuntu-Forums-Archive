---
title: "Zfs, btrfs, ext4"
date: 2008-10-27
forum: The Cafe
---

### Post by BGFG on 2008-10-27
As i read and learn more and with the advent of ZFS and my knowledge that BTRFS is coming.... I no longer find myself looking to ext4 with as much anticipation...

Will btrfs be on equal terms with zfs?
Will linux ever get it's hands oz zfs? (i'm aware of zfs's unique license)
Will reiser4 wither and die ?
Is ext4 really just a corporate upgrade for companies with the ext3 fs ?
(this one i doubt)

Fs gurus, please edify.....

---

### Post by regomodo on 2008-10-27
#

---

### Post by BGFG on 2008-10-27
I'd prefer to run it 'kernel'. but that may be unlikely. Will look into fuse. I'm keeping track of btrfs also. I'm hoping it may be in 9.10 But that may be a bit zealous on my part.

---

### Post by regomodo on 2008-10-27
#

---

### Post by ssam on 2008-10-27
> **BGFG said:**
> 
Will linux ever get it's hands oz zfs? (i'm aware of zfs's unique license)


fat, ntfs, hfs where never GPL'ed by their creators, and they are all in linux. The complaints about CDDL just mean we can't copy and paste ZFS into linux, someone will have to write a new implementation.

The only thing that might stop it is if netapp manage to kill ZFS with patent claims.

---

### Post by zekopeko on 2008-10-27
btrfs looks to be even better than ZFS.
i can remember what site i read that but i think it was LWN.net or something similar.

and i would say that you will first see btrfs somewhere around 10.4 or 10.10. no way is alpha or beta class software be allowed in ubuntu that is so imporant as the filesystem.

---

### Post by BGFG on 2008-10-27
> **zekopeko said:**
> btrfs looks to be even better than ZFS.
i can remember what site i read that but i think it was LWN.net or something similar.

and i would say that you will first see btrfs somewhere around 10.4 or 10.10. no way is alpha or beta class software be allowed in ubuntu that is so imporant as the filesystem.

As i thought, but we can hope...:)
As we 'sit' in here, chatting about btrfs and other such advanced tech, you have to wonder why people still pay for OS'es. I mean, a lot of linux is bleeding edge and they give us it for free.
Colour me spoilt.

---

### Post by flomar on 2009-01-12
Hi,

i asked myself the same question as BGFG. i find the following link to perfectly answer our question: [http://lwn.net/Articles/303814/](http://lwn.net/Articles/303814/)

flo

---

### Post by billgoldberg on 2009-01-12
I doubt things like zfs and btrfs, let alone ext4 will persuade people to use Linux on the desktop market.

I personally am looking out for btrfs and ReiserFS 4, I don't really care much for Zfs and ext4.

---

### Post by sehe on 2009-02-03
> **billgoldberg said:**
> I doubt things like zfs and btrfs, let alone ext4 will persuade people to use Linux on the desktop market.

I personally am looking out for btrfs and ReiserFS 4, I don't really care much for Zfs and ext4.

To me that clearly indicates you haven't taken the time to get to ZFS. How can you not be interested in ZFS, yet be waiting for Btrfs

The overlap is just too much to ignore.

---

### Post by mips on 2009-02-03
> **BGFG said:**
> 
As we 'sit' in here, chatting about btrfs and other such advanced tech, you have to wonder why people still pay for OS'es. I mean, a lot of linux is bleeding edge and they give us it for free.


Most people out there don't even know whan an OS is, never mind a FS. The average person out there using windows won't even know the deifference between FAT32 & NTFS or what it does.

---

### Post by SunnyRabbiera on 2009-02-03
ext4 looks to be the winner here as ZFS doesn't have a GPL friendly license and btrfs is still in alpha.

---

### Post by mips on 2009-02-03
> **SunnyRabbiera said:**
> **ext4 looks to be the winner here** as ZFS doesn't have a GPL friendly license and btrfs is still in alpha.

For now that is ;)

Many people consider ext4 to be a stepping stone to btrfs. I do not see ZFS coming to linux as a kernel module.

For now I'll just carry on using XFS.

---

### Post by gnomeuser on 2009-02-03
> **SunnyRabbiera said:**
> ext4 looks to be the winner here as ZFS doesn't have a GPL friendly license and btrfs is still in alpha.

An official Sun representative was at linux.conf.au and stated there was a serious presure on them to GPL ZFS. Probably due to btrfs and tux3 becoming viable competition and if they want anything to say (and thus reap support money) they need to be in Linux.

---

### Post by BGFG on 2009-02-03
> **gnomeuser said:**
> An official Sun representative was at linux.conf.au and stated there was a serious presure on them to GPL ZFS. Probably due to btrfs and tux3 becoming viable competition and if they want anything to say (and thus reap support money) they need to be in Linux.

makes sense. linux is big in the server market and the major benefits of ZFS and BTRFS are most eident on server platforms.
I need to read up on Tux3

Also, so the ReiserFS is still healthy and in development ?

---

### Post by SunnyRabbiera on 2009-02-03
> **BGFG said:**
> makes sense. linux is big in the server market and the major benefits of ZFS and BTRFS are most eident on server platforms.
I need to read up on Tux3

Also, so the ReiserFS is still healthy and in development ?

Reiser seems to be as dead as its creators wife is...

---

### Post by Grant A. on 2009-02-03
> **SunnyRabbiera said:**
> Reiser seems to be as dead as its creators wife is...

One man at Novell is currently maintaining it due to a contract between Novell and Namesys. However, the contract expires soon and once that happens, it will likely fade away, unless someone forks it.

I want a HAMMER filesystem module. BTW, FAT32 and its ilk are only supported by the Linux kernel by reverse engineered drivers which are licensed under the GPL. Of course, we could always just reverse engineer a ZFS driver for Linux and stick it under the GPL. It would probably be a quick process, considering that ZFS is already under another FOSS license.

---

### Post by BGFG on 2009-02-03
The future looks like BTRFS and tux3 for me. I just want the fastest one :)

---

### Post by ghindo on 2009-02-03
What are the advantages of HAMMER?

---

### Post by Grant A. on 2009-02-03
> **ghindo said:**
> What are the advantages of HAMMER?

It's in alpha, and does almost the same things as ZFS. Not to mention it has a BSD license, so a driver could be converted to the GPL.

---

### Post by cardinals_fan on 2009-02-03
> **ghindo said:**
> What are the advantages of HAMMER?
HAMMER is (in my opinion) the most advanced and powerful file system available... for huge server systems.  I don't really find it worthwhile on my 250 GB desktop disk, but it is awesome.  Read the following:

[http://www.dragonflybsd.org/hammer/index/](http://www.dragonflybsd.org/hammer/index/) <-- a basic overview
[http://www.dragonflybsd.org/hammer/index/hammer.pdf](http://www.dragonflybsd.org/hammer/index/hammer.pdf) <-- the absolute best info available
[http://leaf.dragonflybsd.org/cgi/web-man?command=hammer&section=5](http://leaf.dragonflybsd.org/cgi/web-man?command=hammer&section=5) <-- a man page

---

### Post by cariboo on 2009-02-03
> Hans Reiser was convicted of murder on April 28th, 2008, leaving the future of Reiser4 uncertain. After his arrest, employees of Namesys assured they would continue to work and that the events would not slow down the software development in the immediate future. In order to afford increasing legal fees, Hans Reiser announced on December 21, 2006 that he was going to sell Namesys; as of March 26, 2008, it has not been sold, although the website is unavailable. In January 2008, Edward Shishkin, an employee of and programmer for Namesys, was quoted in a CNET interview saying that "Commercial activity of Namesys has stopped." Shishkin and others continued the development of Reiser4, making source code available from Shishkin's web site, later relocated to kernel.org.

As of August 2008, Reiser4 development still continues without Namesys. However, kernel developer Theodore Ts'o has suggested btrfs as an alternative for those interested in the design ideas of Reiser4.

If anyone is holding their breath waiting for reiser4, I think the wait is going to be very long.

Jim

---

### Post by Grant A. on 2009-02-03
> **cardinals_fan said:**
> HAMMER is (in my opinion) the most advanced and powerful file system available... for huge server systems.  I don't really find it worthwhile on my 250 GB desktop disk, but it is awesome.  Read the following:

[http://www.dragonflybsd.org/hammer/index/](http://www.dragonflybsd.org/hammer/index/) <-- a basic overview
[http://www.dragonflybsd.org/hammer/index/hammer.pdf](http://www.dragonflybsd.org/hammer/index/hammer.pdf) <-- the absolute best info available
[http://leaf.dragonflybsd.org/cgi/web-man?command=hammer&section=5](http://leaf.dragonflybsd.org/cgi/web-man?command=hammer&section=5) <-- a man page

I wouldn't call it the most powerful, as it requires clean-up every night to keep functional.

---

### Post by mips on 2009-02-04
> **BGFG said:**
> The future looks like BTRFS and tux3 for me. I just want the fastest one :)

And use the least amount of CPU resources ;)

---

### Post by cepal on 2009-07-31
> **mips said:**
> For now that is ;)

Many people consider ext4 to be a stepping stone to btrfs. I do not see ZFS coming to linux as a kernel module.

For now I'll just carry on using XFS.

You probably don't face hard resets on your systems or have good backups. As this system is corrupting files on hard resets, esp. if you are not careful and boot the system before first doing xfs_repair (booting from some external media)! It journals only metadata, thus the FS seems clean even when you have dirty data! Otherwise, yet with it's age, it's a very nice and damn quick FS, no question about that... (one more minus is "no downsizing" so you can only grow but what the heck, this is exactly as it happens in the real life).

FYI VXFS is pretty cool, apart the bugs it has :-(, which become nightmares when you use the FS for thingy it wasn't intended to be used for (like incredibly huge amount of small files being created, written & destroyed constantly, yet tens of thousands in one folder - this is what VXFS doesn't survive and sometimes is just fine with fsadm -edED, sometimes needs remounting to free up the space of the many removed small files...). 

I am really hungry for BTRFS or TUX3 whichever comes first to "stable" state. EXT4 seems to me to be like improving a dead horse's performance by giving it a platinum stifle shoes :-(. Even already EXT3 was that case - adding a journal file to non-natively-journaled EXT2. This conservatism in Linux world surprised me a lot. Maybe if they just developed BTRFS under EXT5 name, it would have much more popularity!

CePal

---

### Post by RiceMonster on 2009-07-31
The dead return to life...

---

### Post by Eisenwinter on 2009-07-31
> **ricemonster said:**
> the dead return to life...
ohnoes! Zombies!!!

---

### Post by SunnyRabbiera on 2009-07-31
I wonder about Tux3, I know it just came out but so did EXT4.
EXT4 seems to be getting the attention right now, and with Reiser out of the game maybe Tux3 can take up the space.
But I am not aware of any linux distro that uses it.

---

### Post by Regenweald on 2009-07-31
I look forward to tux3 and btrfs. OpenSolaris and FreeBSD offer zfs anyway :)

---

### Post by thisllub on 2009-07-31
60 second snapshots are God's gift to disk manufacturers.

---

### Post by jrusso2 on 2009-07-31
Its called NIH or not invented here.  Thats why so many user love ext filesystems even though they seem to result in the most data loss and are the biggest pains to use.

---

### Post by ghindo on 2009-07-31
> **jrusso2 said:**
> Its called NIH or not invented here.  Thats why so many user love ext filesystems even though they seem to result in the most data loss and are the biggest pains to use.What do you mean by that?  The ext filesystems seem to be among the most stable and reliable filesystems out there.  (At the very least, *I've* never had any trouble with them.)

---

### Post by Regenweald on 2009-07-31
> **ghindo said:**
> What do you mean by that?  The ext filesystems seem to be among the most stable and reliable filesystems out there.  (At the very least, *I've* never had any trouble with them.)

Must concur, I cannot speak for the enterprise environment, but for the desktop they perform well. In any case around the corner there be dragons on the way :)

---

### Post by FuturePilot on 2009-07-31
> **ghindo said:**
> What do you mean by that?  The ext filesystems seem to be among the most stable and reliable filesystems out there.  (At the very least, *I've* never had any trouble with them.)

> **Regenweald said:**
> Must concur, I cannot speak for the enterprise environment, but for the desktop they perform well. In any case around the corner there be dragons on the way :)

I also agree. I've never had any issues with Ext3. I've had hard resets and power failures on Ext3 and nothing was lost or damaged. I cannot say the same about other filesystems though.

---

### Post by cepal on 2009-07-31
> **Regenweald said:**
> Must concur, I cannot speak for the enterprise environment, but for the desktop they perform well. In any case around the corner there be dragons on the way :)

Well not sure about performance (or performance increase pottential) but from the stability/reliability point of view, the EXT3 is ok... But it's also because it absolutely doesn't provide any advanced options, like online defragmentation, snapshots (well there are tools for snapshotting ext3, but I mean internally within the FS), RAID and multi-volume layots (there is LVM2 for the multi-volume and related and MD for RAID but hey why don't we have FS which directly internally contain this, that'd be much more reliable and efficient, once there is a reliable/stable/efficient code for it - and that's exactly what I expect BTRFS to be (or TUX or whichver "next generation" FS))...

If you take a really very old cars and motorbikes, they tend to be much more reliable && easy to fix in comparison to the nowadays overtechnisized machines, but then tell me, why no one wants to have a Citroen 2CV as a family car? I am not claiming for overcomplicated FS (hey, ever heard of GFS?), but EXT* is a stone-age, thats how it is...

---

### Post by jrusso2 on 2009-07-31
I have been uisng Linux for 13 years the only times I lost data due to power outage wa either ext2 or ext3.  Also its a pain in the *** if you have a server or like hard drive with that filestyem checkk can take a very long time.

---

### Post by Regenweald on 2009-07-31
Hopefully, with tux3 and btrfs, such woes will be of yesteryear.

---

### Post by moster on 2009-08-01
Whatever may happend only one thing is sure. It will never be boring :)

---

### Post by papangul on 2009-08-01
> **cepal said:**
> You probably don't face hard resets on your systems or have good backups. As this system is corrupting files on hard resets, esp. if you are not careful and boot the system before first doing xfs_repair (booting from some external media)! It journals only metadata, thus the FS seems clean even when you have dirty data! 
I have been using xfs for a long time and was not aware of these facts. I have never done 'xfs_repair' manually, although I have three xfs partitions. 

Earlier I had jfs and everytime I had an improper shutdown, the jfs partitions would not be mounted during the next boot. I switched to xfs and was just happy that the os boots fast after doing a hard reboot, with all it's partitions.

Thanks for the info, you have opened my eyes!

---

### Post by jalyst on 2009-08-17
Geez there's soo many potential contenders for the _next-gen_ throne now:

btrfs, nilfs32, tux3...

And now that Oracle owns Sun they'll prolly GPL ZFS! I dunno where to start! 

There'll have to be one 'officially sanctioned' fs eventually, I wonder which one it'll be!

---

### Post by ssam on 2009-08-17
remember that btrfs is not designed to be faster than ext3/4, its designed to have more features.

---

### Post by kk0sse54 on 2009-08-17
> **jalyst said:**
> 
And now that Oracle owns Sun they'll prolly GPL ZFS! I dunno where to start! 
I don't see why they should but then again I'm not restricted by it's license so I've been able to use it. It will be more intresting to see if the ZFS on FUSE project ever reaches the capacity of ntfs-3g.

> There'll have to be one 'officially sanctioned' fs eventually, I wonder which one it'll be!

Probably not. A preference maybe, but nothing more.

---

### Post by djurny on 2009-12-20
> **cepal said:**
> You probably don't face hard resets on your systems or have good backups. As this system is corrupting files on hard resets, esp. if you are not careful and boot the system before first doing xfs_repair (booting from some external media)! It journals only metadata, thus the FS seems clean even when you have dirty data! Otherwise, yet with it's age, it's a very nice and damn quick FS, no question about that... (one more minus is "no downsizing" so you can only grow but what the heck, this is exactly as it happens in the real life).

FYI VXFS is pretty cool, apart the bugs it has :-(, which become nightmares when you use the FS for thingy it wasn't intended to be used for (like incredibly huge amount of small files being created, written & destroyed constantly, yet tens of thousands in one folder - this is what VXFS doesn't survive and sometimes is just fine with fsadm -edED, sometimes needs remounting to free up the space of the many removed small files...). 

I am really hungry for BTRFS or TUX3 whichever comes first to "stable" state. EXT4 seems to me to be like improving a dead horse's performance by giving it a platinum stifle shoes :-(. Even already EXT3 was that case - adding a journal file to non-natively-journaled EXT2. This conservatism in Linux world surprised me a lot. Maybe if they just developed BTRFS under EXT5 name, it would have much more popularity!

CePalext3 can indeed also journal data, but that still does not guarantee that the actual data is consistent on disk :) the zeroing-out of files on mount after powerfailure seems like a safety feature of xfs, and when you think about it, what use is a file with 40% of its contents kaputt? i mean, i saw this in real life and believe me, after a fsck.ext3 you don't get what you would expect ;)

for me, i cant wait to toy around with btrfs.. :)

---

### Post by Xbehave on 2009-12-20
> **djurny said:**
> ext3 can indeed also journal data, but that still does not guarantee that the actual data is consistent on disk :) the zeroing-out of files on mount after powerfailure seems like a safety feature of xfs, and when you think about it, what use is a file with 40% of its contents kaputt? i mean, i saw this in real life and believe me, after a fsck.ext3 you don't get what you would expect ;)

for me, i cant wait to toy around with btrfs.. :)
btrfs is already in mainline, i use it for all my data partitions (i don't have anything valuable), online fsck is pretty nice, I'm not sure what the performance is like but I'll probably move all my partitions to it whenever it matches ext. For the uninformed btrfs takes part of reiserfs (a very fast filesystem) and runs with it so it should end up much faster than ext even with all the features.

I think the big break will be when file manager start transparently integrating btrfs features, forget about trash cans, versioning, etc just let the fs handle it at a minimal cost and the filebrowser show them when required (does this happen with zfs on solaris?)

---

### Post by jalyst on 2009-12-21
I wonder when it'll start becoming standard with major ubuntu releases, still some way off?
Mainline is cool, but main FS by default is more confidence inspiring :)

---

### Post by Exodist on 2009-12-21
> **jalyst said:**
> I wonder when it'll start becoming standard with major ubuntu releases, still some way off?
Mainline is cool, but main FS by default is more confidence inspiring :)
Ext4 is now default on Karmic and above.

---

### Post by jrusso2 on 2009-12-21
> **cepal said:**
> You probably don't face hard resets on your systems or have good backups. As this system is corrupting files on hard resets, esp. if you are not careful and boot the system before first doing xfs_repair (booting from some external media)! It journals only metadata, thus the FS seems clean even when you have dirty data! Otherwise, yet with it's age, it's a very nice and damn quick FS, no question about that... (one more minus is "no downsizing" so you can only grow but what the heck, this is exactly as it happens in the real life).

FYI VXFS is pretty cool, apart the bugs it has :-(, which become nightmares when you use the FS for thingy it wasn't intended to be used for (like incredibly huge amount of small files being created, written & destroyed constantly, yet tens of thousands in one folder - this is what VXFS doesn't survive and sometimes is just fine with fsadm -edED, sometimes needs remounting to free up the space of the many removed small files...). 

I am really hungry for BTRFS or TUX3 whichever comes first to "stable" state. EXT4 seems to me to be like improving a dead horse's performance by giving it a platinum stifle shoes :-(. Even already EXT3 was that case - adding a journal file to non-natively-journaled EXT2. This conservatism in Linux world surprised me a lot. Maybe if they just developed BTRFS under EXT5 name, it would have much more popularity!

CePal

I think its a case of NIH, not invented here, but even Linus acknowledges ext 4 is inadequate file system for a large enterprise server.

---

### Post by Xbehave on 2009-12-21
> **jrusso2 said:**
> I think its a case of NIH, not invented here, but even Linus acknowledges ext 4 is inadequate file system for a large enterprise server.
There have always been good filesystems for Linux (reiserfs, xfs, JFS), but ext is maintained by the people cose to the kernel and as a result it gets the best support, ext is a stable rock. Linus acknowledged that ext4 wasn't ready for enterprise yet, but i don't think he meant it never will be. 

Ext4 is essentially tweaking performance on a really old filesystem, but lots of people value the stability from essentially still being on an improved ext2 (your talking about trillions of hours of testing) over the speed it costs them.

---

### Post by jalyst on 2009-12-21
yeah i know, but btrfs would be cooler :)

> **Exodist said:**
> Ext4 is now default on Karmic and above.

---

### Post by jamessnell on 2010-04-20
> **Xbehave said:**
> There have always been good filesystems for Linux (reiserfs, xfs, JFS), but ext is maintained by the people cose to the kernel and as a result it gets the best support, ext is a stable rock. Linus acknowledged that ext4 wasn't ready for enterprise yet, but i don't think he meant it never will be. 

Ext4 is essentially tweaking performance on a really old filesystem, but lots of people value the stability from essentially still being on an improved ext2 (your talking about trillions of hours of testing) over the speed it costs them.

Beautifully put. I completely fall in to the category of valuing stability over features or performance. My file server has an LVM across 7 hard drives, if some stupid error case corrupted my file system, well, I'd be pretty sad. I've actually been using ReiserFS for this for years, though looks like I'll be migrating to Ext4 now because ReiserFS supposedly is limited to 16TB.

I'm very interested in the up and coming stuff, but for now, I'll have to let others test out and solidify the new stuff..

Stability FTW.

---

### Post by jalyst on 2010-04-21
but surely BTRFS is getting pretty solid/stable now?

---

### Post by kairuri on 2010-05-21
> **jalyst said:**
> but surely BTRFS is getting pretty solid/stable now?

Try it out for yourself - it is in Lucid:
# apt-get install btrfs-tools

Try it on a USB drive it you don't want to commit real data.


# wajig list-files btrfs-tools
/.
/usr
/usr/share
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/mkfs.btrfs.8.gz
/usr/share/man/man8/btrfsctl.8.gz
/usr/share/man/man8/btrfsck.8.gz
/usr/share/man/man8/btrfs-image.8.gz
/usr/share/man/man8/btrfs-show.8.gz
/usr/share/doc
/usr/share/doc/btrfs-tools
/usr/share/doc/btrfs-tools/README.Debian
/usr/share/doc/btrfs-tools/copyright
/usr/share/doc/btrfs-tools/changelog.Debian.gz
/sbin
/sbin/btrfsctl
/sbin/mkfs.btrfs
/sbin/btrfs-debug-tree
/sbin/btrfs-show
/sbin/btrfs-vol
/sbin/btrfsck
/sbin/btrfs-convert
/sbin/btrfs-image
/sbin/btrfstune
/sbin/fsck.btrfs

---

### Post by jalyst on 2010-05-22
yeah i intend to
[http://ubuntuforums.org/showthread.php?t=1463862](http://ubuntuforums.org/showthread.php?t=1463862)
thanks!

---

### Post by madjr on 2010-05-22
Btrfs May Be The Default File-System In Ubuntu 10.10

[http://www.phoronix.com/scan.php?page=news_item&px=ODI1Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODI1Mg)


as well as fedora and Meego

---

### Post by jalyst on 2010-05-24
yeah i hope it gets way more traction, and starts solidfyng much more quickly, t'would be sweet!

---

