---
title: "ZFS coming to Linux (Ubuntu)?"
date: 2008-06-09
forum: The Cafe
---

### Post by BassKozz on 2008-06-09
Could [ZFS]("http://en.wikipedia.org/wiki/ZFS") be coming to Linux (Ubuntu)?
Check out this blog entry by the creator of ZFS sitting down for a beer with Linus Torvalds: [http://blogs.sun.com/bonwick/entry/casablanca](http://blogs.sun.com/bonwick/entry/casablanca)

I know this is just speculation right now, but I am dieing to figure out what all of this is about.  I've searched the internet to find out more information on this but my ninja-Google skillz just aren't that great.  Does anyone have any further information on this?

---

### Post by billgoldberg on 2008-06-09
ZFS on Linux could be great,

but it could also mean Linus is going to work for/with Sun.

---

### Post by Methuselah on 2008-06-09
I totally don't understand that page.
Pictures, Peanut butter, then speculation out of the blue!?
I guess you have to be in the know.

---

### Post by BassKozz on 2008-06-09
> **Methuselah said:**
> I totally don't understand that page.
Pictures, Peanut butter, then speculation out of the blue!?
I guess you have to be in the know.

Yah, I wish someone "in the know" would post some useful info on this.

---

### Post by FuturePilot on 2008-06-09
> **Methuselah said:**
> I totally don't understand that page.
Pictures, Peanut butter, then speculation out of the blue!?
I guess you have to be in the know.

Must be an inside joke...:|

---

### Post by mips on 2008-06-09
I do not see it happening unless Sun changes the license as the current license is uncompatible with the GPL.

---

### Post by cardinals_fan on 2008-06-09
> **mips said:**
> I do not see it happening unless Sun changes the license as the current license is uncompatible with the GPL.
...even though it's open source.

---

### Post by ghindo on 2008-06-09
ZFS will probably eventually come to Linux, but not for a while, I would guess.

---

### Post by dmitrijledkov on 2008-06-09
> **billgoldberg said:**
> ZFS on Linux could be great,

but it could also mean Linus is going to work for/with Sun.

Linus is a git. He will not not work for/with Sun, Sun will work for him, but he will take credit. Some another Sun blogger, points to that post with a title "ZFS pics".

:lolflag: :

If you stare at the pictures very closely you can see a slight trace of a flying EeePC, which Linus used to create one more git tree which has ZFS integrated and it is compiling while they two are out on the terrace.

---

### Post by ghindo on 2008-06-09
What advantages would ZFS have over Ext3?  I've heard a lot of positive talk about ZFS, but rarely any negative talk.  However, I just read this on another forum:> There are plenty of things in ZFS that would suck to have to deal with every day. For instance, all of the redundancy it affords comes at the cost of increased disk usage -- a 1GB file can take up 2GB or more of disk. Each FS attribute that isn't built into ZFS uses an additional *128kb* per file -- so every 4kb file with half a dozen attributes (of which any modern OS has tens of thousands) suddenly takes up over a MB.

Having an expanding storage pool is cool, but the problem in the current implementation is that you can't *shrink* the pool. If you add a disk to your system you *can never remove it* without reformatting the entire array. In a server maybe that's fine, but the hell if I'm going to deal with that **** on my desktopIs this true?

---

### Post by LightB on 2008-06-09
> **ghindo said:**
> What advantages would ZFS have over Ext3?  I've heard a lot of positive talk about ZFS, but rarely any negative talk.  However, I just read this on another forum:Is this true?

Yes, I'd guess it is true. I've heard similar things. ZFS was created to suit very large drives and databases. Looks like people don't know what they're talking about when they go on about ZFS on their machines. I'd be willing to bet that on a regular x86 PC with SATA or IDE drives, even JFS beats the pants off ZFS in performance.

---

### Post by BassKozz on 2008-06-10
> There are plenty of things in ZFS that would suck to have to deal with every day. For instance, all of the redundancy it affords comes at the cost of increased disk usage -- a 1GB file can take up 2GB or more of disk. Each FS attribute that isn't built into ZFS uses an additional *128kb* per file -- so every 4kb file with half a dozen attributes (of which any modern OS has tens of thousands) suddenly takes up over a MB.

Having an expanding storage pool is cool, but the problem in the current implementation is that you can't *shrink* the pool. If you add a disk to your system you *can never remove it* without reformatting the entire array. In a server maybe that's fine, but the hell if I'm going to deal with that **** on my desktop
Interesting, I didn't know that you couldn't down-size a ZFS array :confused:

Thanks for the info "ghindo" you mind providing a link to that forum/thread?
-BassKozz

---

### Post by ghindo on 2008-06-10
> **BassKozz said:**
> Interesting, I didn't know that you couldn't down-size a ZFS array :confused:

Thanks for the info "ghindo" you mind providing a link to that forum/thread?
-BassKozzIt's a private forum :(

---

### Post by BassKozz on 2008-06-10
> **BassKozz said:**
> Could [ZFS]("http://en.wikipedia.org/wiki/ZFS") be coming to Linux (Ubuntu)?
Check out this blog entry by the creator of ZFS sitting down for a beer with Linus Torvalds: [http://blogs.sun.com/bonwick/entry/casablanca](http://blogs.sun.com/bonwick/entry/casablanca)

I know this is just speculation right now, but I am dieing to figure out what all of this is about.  I've searched the internet to find out more information on this but my ninja-Google skillz just aren't that great.  Does anyone have any further information on this?
Nobody knows what this really means, its all still just speculation right now?:confused:?

---

### Post by kwagner on 2008-06-23
ZFS is already working just great on Linux (Ubuntu 8.04 here) with FUSE :)
As a matter of fact, my /home is already mounted on a ZFS slice:

karl@karl-workstation:/$ uname -a
Linux karl-workstation 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

karl@karl-workstation:/$ sudo zpool upgrade -v
This system is currently running ZFS pool version 10.

The following versions are supported:

VER  DESCRIPTION
---  --------------------------------------------------------
 1   Initial ZFS version
 2   Ditto blocks (replicated metadata)
 3   Hot spares and double parity RAID-Z
 4   zpool history
 5   Compression using the gzip algorithm
 6   bootfs pool property
 7   Separate intent log devices
 8   Delegated administration
 9   refquota and refreservation properties
 10  Cache devices
For more information on a particular version, including supported releases, see:

[http://www.opensolaris.org/os/community/zfs/version/N](http://www.opensolaris.org/os/community/zfs/version/N)

Where 'N' is the version number.



karl@karl-workstation:/$ sudo zfs upgrade -v
The following filesystem versions are supported:

VER  DESCRIPTION
---  --------------------------------------------------------
 1   Initial ZFS filesystem version
 2   Enhanced directory entries
 3   Case insensitive and File system unique identifer (FUID)

For more information on a particular version, including supported releases, see:

[http://www.opensolaris.org/os/community/zfs/version/zpl/N](http://www.opensolaris.org/os/community/zfs/version/zpl/N)

Where 'N' is the version number.


karl@karl-workstation:/$ sudo zfs upgrade -v
The following filesystem versions are supported:

VER  DESCRIPTION
---  --------------------------------------------------------
 1   Initial ZFS filesystem version
 2   Enhanced directory entries
 3   Case insensitive and File system unique identifer (FUID)

For more information on a particular version, including supported releases, see:

[http://www.opensolaris.org/os/community/zfs/version/zpl/N](http://www.opensolaris.org/os/community/zfs/version/zpl/N)

Where 'N' is the version number.



karl@karl-workstation:/$ sudo zfs list

NAME             USED  AVAIL  REFER  MOUNTPOINT
tank            48.4G  15.1G    18K  /tank
tank/home       48.4G  15.1G    19K  /home
tank/home/karl  48.4G  15.1G  48.4G  /home/karl



Just follow the instructions here ;)

[http://www.wizy.org/wiki/ZFS_on_FUSE](http://www.wizy.org/wiki/ZFS_on_FUSE)

Cheers!

---

### Post by bufsabre666 on 2008-06-23
personally im more interested in ext4 and when ubuntu is ganna let you use it as the root folder, although its yet to have a stable release it looks promising

---

### Post by ghindo on 2008-06-23
kwanger:  How is ZFS through FUSE working?  I hear that running it through FUSE creates a performance hit.  How big is the harddrive you're using ZFS on?

---

### Post by Methuselah on 2008-06-23
I used FreeBSD 7 (which comes with ZFS)  and never touched ZFS.

---

### Post by kwagner on 2008-06-23
> **ghindo said:**
> kwagner:  How is ZFS through FUSE working?  I hear that running it through FUSE creates a performance hit.  How big is the harddrive you're using ZFS on?

Im running on a Athlon64 2.4Ghz machine, with an old hard drive. An 82GB  Hitachi DeskStar IDE drive.

As far as performance, I find it very good.
Here's a quick test on my home dir:


karl@karl-workstation:~$ pwd
/home/karl
karl@karl-workstation:~$ 
karl@karl-workstation:~$ time sh -c "dd if=/dev/zero of=bigfile bs=8k count=250000 && sync"
250000+0 records in
250000+0 records out
2048000000 bytes (2.0 GB) copied, 47.2331 s, 43.4 MB/s

real	0m47.353s
user	0m0.188s
sys	0m3.648s


And now I move to /tmp, which is EXT3, and run the same test:

karl@karl-workstation:/tmp$ pwd
/tmp
karl@karl-workstation:/tmp$ time sh -c "dd if=/dev/zero of=bigfile bs=8k count=250000 && sync"
250000+0 records in
250000+0 records out
2048000000 bytes (2.0 GB) copied, 82.6251 s, 24.8 MB/s

real	1m25.534s
user	0m0.112s
sys	0m5.516s


He!, what do you know, it's faster than on EXT3 :)
Probably because I have set compression=on, on the /home zfs pool, so I'm really happy with performance. I even ran the 'ztest' to validate the framework, and it passes all results without errors. I really salute the SUN team, and Ricardo Correia, the person who did the Linux port to FUSE :)

BTW, I'm using "Trunk" version of zfs-fuse, from the mercurial repository. Link on my previous post.

---

### Post by kwagner on 2008-06-23
> **Methuselah said:**
> I used FreeBSD 7 (which comes with ZFS)  and never touched ZFS.
We use FreeBSD 7 (Release) with ZFS at work on a production machine, running PostgreSQL.
It performs flawlessly. 
At least it has for the past couple of months or so, with close to 1M transactions per 24H. So it's not bad at all :)

---

### Post by maniacmusician on 2008-06-23
> **BassKozz said:**
> Yah, I wish someone "in the know" would post some useful info on this.
You don't really have to be "in the know," you just have to read carefully and use good old deductive reasoning. 

The blog, as mentioned by OP, belongs to one Jeff Bonwick, the creator of ZFS. If you look at the picture at the top of the page, next to the name of the blog, you'll see that it matches one of the people in the pictures of the two people talking. That man is obviously Jeff Bonwick. 

The other, as you can probably gather from the OP's post and the comments on that blog, is Linus Torvalds (invented the Linux kernel, yada yada). That particular blog post is filed under the tag "ZFS." Putting all these things together is making people wonder, and leading them to guesses such as "ZFS is coming to Linux," or "Linus is going to work for Sun."

As for ZFS on linux, though already mentioned, there's only 2 ways it can happen. One is to use the FUSE implementation of it, which seems to be working quite well. The other is for Sun to change the license to GPL. The latter has both benefits and consequences for Sun, and it's really somewhat hard to predict which way they'll go. When I think about it, I keep flip-flopping, so I've stopped doing that. I'm probably not going to use it either way, unless it comes installed by default in something I happen to be using.

---

### Post by mips on 2008-06-23
Oh, and who would want to use it on a desktop machine anyway, just to much?

I see a good place for it on servers and other production boxes but for the normal desktop user it seems over the top.

Long live XFS!!! :)

---

### Post by Masoris on 2008-06-23
I really waiting this because ZFS support compressed file system. That is one Windows have, Linux doesn't have. I want to save my disk space.

---

### Post by maniacmusician on 2008-06-23
> **mips said:**
> Oh, and who would want to use it on a desktop machine anyway, just to much?

I see a good place for it on servers and other production boxes but for the normal desktop user it seems over the top.

Long live XFS!!! :)
I wouldn't know anything about XFS, but I can certainly think of cases in which ZFS could be useful on a desktop machine. Many users (such as me, for example) have storage capacities approaching a terabyte and up. Some of us actually manage to use a large amount of it :) 

In this scenario, I can certainly appreciate the availability of pooled storage, FS compression, and redundancy (as long as I can choose in the instances in which it occurs). However, with the way I have my backups and folder heirarchy set up right now, I don't really have any incentive to change it, unless it comes default with something I'm using, and gives me ample (yet easy) control over it.

But I see your point, the scenario I gave certainly isn't a "normal" desktop, though it is growing more common.

---

### Post by the_darkside_986 on 2008-06-23
Didn't Sun receive a patent lawsuit over ZFS? What happened with that case? FLOSS receives enough patent rattling and threats everyday, no need to add to that.

---

### Post by BassKozz on 2008-06-23
> **bufsabre666 said:**
> personally im more interested in ext4 and when ubuntu is ganna let you use it as the root folder, although its yet to have a stable release it looks promising
What does ext4 have that ZFS doesn't? Just curious

> **Methuselah said:**
> I used FreeBSD 7 (which comes with ZFS)  and never touched ZFS.
Good for you, but not really a helpful post in this thread. :-s
Some people won't use it, but that doesn't mean it shouldn't be available for the people who will.
> **kwagner said:**
> Im running on a Athlon64 2.4Ghz machine, with an old hard drive. An 82GB  Hitachi DeskStar IDE drive.

As far as performance, I find it very good.
Here's a quick test on my home dir:


karl@karl-workstation:~$ pwd
/home/karl
karl@karl-workstation:~$ 
karl@karl-workstation:~$ time sh -c "dd if=/dev/zero of=bigfile bs=8k count=250000 && sync"
250000+0 records in
250000+0 records out
2048000000 bytes (2.0 GB) copied, 47.2331 s, 43.4 MB/s

real	0m47.353s
user	0m0.188s
sys	0m3.648s


And now I move to /tmp, which is EXT3, and run the same test:

karl@karl-workstation:/tmp$ pwd
/tmp
karl@karl-workstation:/tmp$ time sh -c "dd if=/dev/zero of=bigfile bs=8k count=250000 && sync"
250000+0 records in
250000+0 records out
2048000000 bytes (2.0 GB) copied, 82.6251 s, 24.8 MB/s

real	1m25.534s
user	0m0.112s
sys	0m5.516s


He!, what do you know, it's faster than on EXT3 :)
Probably because I have set compression=on, on the /home zfs pool, so I'm really happy with performance. I even ran the 'ztest' to validate the framework, and it passes all results without errors. I really salute the SUN team, and Ricardo Correia, the person who did the Linux port to FUSE :)

BTW, I'm using "Trunk" version of zfs-fuse, from the mercurial repository. Link on my previous post.
This test however doesn't show results for a RAIDZ or a RAIDZ2 configuration.  My main goal is to use ZFS for redundancy (replace mdadm), I would like to see how the FUSE port is working with a RAIDZ config?

> **mips said:**
> Oh, and who would want to use it on a desktop machine anyway, just to much?

I see a good place for it on servers and other production boxes but for the normal desktop user it seems over the top.

Long live XFS!!! :)
Have you ever tried using mdadm, if so have you seen how much easier it is to implement a redundant array of disks using ZFS?

---

I recommend everyone have a look at this Blog post: [http://breden.org.uk/2008/03/02/a-home-fileserver-using-zfs/](http://breden.org.uk/2008/03/02/a-home-fileserver-using-zfs/)
Very informative.

---

### Post by ddales on 2008-07-23
Yes and no.

False.  The file size comments are not accurate.  A 1GB file takes up 1GB of space.

True.  You cannot shrink pools.  But then again, why would you want to?  ZFS is intended for mass storage areas, not operating system volumes.  It's intended to scale upwards not downwards.

---

### Post by BassKozz on 2008-07-23
Still no updates from Jeff Bonwick yet?
> All I can say for the moment is... stay tuned.
This is killing me :-k

---

### Post by kwagner on 2008-07-27
> **ddales said:**
> ZFS is intended for mass storage areas, not operating system volumes.  It's intended to scale upwards not downwards.
Nope. Not really.
It's also perfectly reasonable to use it as main system, specifically because of checksummed data on everything.
So silent corruption cannot happen, as you will know if you *scrub* the system once in a while. This is something Linux doesn't have with any of the  currently existing filesystem.
And BTW, I know this is Ubuntu forums, but I would like to add some ZFS/PCBSD breaking news.
I just downloaded the ALPHA version of PCBSD 7, and what do you know, ZFS is on the ROOT file system!!!!! I'm writing this post with Firefox 3 on it right now.
Yep, you heard it right. I selected "ZFS Experimental"  for the file system, and I was stunned when the system booted and I saw this: 

> [karl@pcbsd /usr/home/karl]$ mount
**ad0s1e/root on / (zfs, local)**
devfs on /dev (devfs, local)
/dev/ad0s1a on /bootdir (ufs, local)
linprocfs on /compat/linux/proc (linprocfs, local)
procfs on /proc (procfs, local)
/dev/md0 on /tmp (ufs, local)

Time for some benchmarks ;)
But I have to say that it's looking VERY impressive!
The ISO images are here: ftp.pcbsd.org under pub/alpha-isos/i386
I instaled the DVD image.

---

### Post by dicecca112 on 2008-07-27
> **ghindo said:**
> What advantages would ZFS have over Ext3?  I've heard a lot of positive talk about ZFS, but rarely any negative talk.  However, I just read this on another 
forum:Is this true?

Yes and no, it all depends on the frag size, ZFS does have its advantages, but its current implementation in Solaris is terrible

---

### Post by BassKozz on 2008-09-19
Still no updated from [Jeff Bonwick]("http://blogs.sun.com/bonwick/") yet :(

---

### Post by regomodo on 2008-09-19
#

---

### Post by anothermikemiller on 2009-02-02
> As for ZFS on linux, though already mentioned, there's only 2 ways it can happen. One is to use the FUSE implementation of it, which seems to be working quite well. The other is for Sun to change the license to GPL. The latter has both benefits and consequences for Sun, and it's really somewhat hard to predict which way they'll go. When I think about it, I keep flip-flopping, so I've stopped doing that. I'm probably not going to use it either way, unless it comes installed by default in something I happen to be using.

I found some information on this.  Apparently the GPL would have to make an exception for ZFS, not the other way around. Debian apparently pissed of at least one of the authors of ZFS with a GPL descision and they decided to go with an incompatible license on PURPOSE!
This was on the wiki:

> GPL Incompatibility Controversy

In the words of Danese Cooper, who is no longer with Sun, one of the reasons for basing the CDDL on the Mozilla license was that the Mozilla license is GPL-incompatible. Cooper stated, at the 6th annual Debian conference, that the engineers who had written the Solaris kernel requested that the license of OpenSolaris be GPL-incompatible. "Mozilla was selected partially because it is GPL incompatible. That was part of the design when they released OpenSolaris. [...] the engineers who wrote Solaris [...] had some biases about how it should be released, and you have to respect that".[6]

Simon Phipps (Sun's Chief Open Source Officer), who was present at the time and who had introduced Ms. Cooper as "the one who actually wrote the CDDL",[7] made no comment at the time. Afterward, in September 2006, Phipps rejected Cooper's assertion.[8]

The incompatibility was also demonstrated by a controversy behind a partial relicensing of cdrtools to the CDDL (which had been previously all GPL), which was declared legally "undistributable" by the Debian project because the build system was licensed under the CDDL, while the GPL requires that all build systems and scripts also be licensed under the GPL, thus causing an incompatibility that violates the license.[9]

---

### Post by ricojonah on 2009-10-27
If Sun ever releases ZFS under the GPL, wouldn't that put OpenSolaris in jeopardy of becoming obsolete or unnecessary? Forgive me; I'm very new to understanding Solaris & OpenSolaris, but my brief impression of *Solaris is that ZFS and DTrace are the only major things helping it to distinguish itself from the crowd (At least from a technical standpoint).

While I'd love to have my Ubuntu server running on a ZFS filesystem (imagine that flexibility and power!), I can't help but wonder if that could ultimately put Sun at a huge disadvantage for marketing its Solaris platform.

In the meantime, I'm playing around a little with Nexenta (OpenSolaris + debian package support - 700MB of memory bloat). 

Does anyone have any thoughts about my question, or about Nexenta?

---

### Post by oobuntoo on 2009-10-28
Last I heard, Sun was about to be bought by Oracle. If and when that became reality, there is a possiblity that Oracle will release ZFS under GPL. Ironically, that would put Btrfs and ZFS in direct competition, since Oracle is also developing Btrfs. Maybe they should just combine the two where possible.

---

### Post by SunnyRabbiera on 2009-10-28
> **oobuntoo said:**
> Last I heard, Sun was about to be bought by Oracle. If and when that became reality, there is a possiblity that Oracle will release ZFS under GPL. Ironically, that would put Btrfs and ZFS in direct competition, since Oracle is also developing Btrfs. Maybe they should just combine the two where possible.

Nah I think ZFS will get phased out in favor of Btrfs.

---

### Post by toupeiro on 2009-10-28
Sad to say it, but I think this has already officially happened.  RIP ZFS.


At first I thought this oracle buyout was going to be a good thing.  Turns out they have NO IDEA how to manage suns portfolio so they're just going to kill it.

EDIT:  Apparently this only applies to Apples ZFS project at this time, I was misinformed.

---

### Post by handy on 2009-10-28
I much prefer the OpenBFS to ZFS.

Apart from anything else, it isn't slow like ZFS.

Here is an old google vid' on Haiku; which may very well blow your mind, when it comes to the details on the OpenBFS... :)

[http://video.google.com/videoplay?docid=236331448076587879#](http://video.google.com/videoplay?docid=236331448076587879#)

---

### Post by SunnyRabbiera on 2009-10-28
> **handy said:**
> I much prefer the OpenBFS

Is it possible to port it to linux though?

---

### Post by handy on 2009-10-28
> **SunnyRabbiera said:**
> Is it possible to port it to linux though?

I certainly hope so. ?

I expect it will get here, that's not me speaking from a technical understanding though...

---

### Post by jdrodrig on 2009-10-29
> **ricojonah said:**
> If Sun ever releases ZFS under the GPL, wouldn't that put OpenSolaris in jeopardy of becoming obsolete or unnecessary? Forgive me; I'm very new to understanding Solaris & OpenSolaris, but my brief impression of *Solaris is that ZFS and DTrace are the only major things helping it to distinguish itself from the crowd (At least from a technical standpoint).


Does anyone have any thoughts about my question, or about Nexenta?

Well OpenSolaris also pushes SMF, Zones (virtualization with only one kernel loaded) and Self-healing stuff as their comparative advantage....

after one month using, I just love my ZFS pools....it is like a server-quality-storage for dummies (I am the dummy!)

---

