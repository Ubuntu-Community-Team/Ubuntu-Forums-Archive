---
title: "The beginning of an end of JFS &amp; XFS"
date: 2006-09-08
forum: The Cafe
---

### Post by The Keeper on 2006-09-08
The past year has not been good to SGI, the first news of SGI's bankruptcy were airing sometime July last year, and similar news aired several times this year. In light of these news, even if SGI manages to avoid bankruptcy, it is unlikely that they will continue to fund XFS' active development.

Today I had the pleasure of briefly chat with one of IBM's JFS developers. He said that IBM no longer had any interest to continue supporting and funding JFS development because the big player Red Hat only supports ext3, and that SuSe is planning to also drop JFS support from its enterprise products as well. And when the big enterprise products don't support JFS, it's not viable to continue developing an unsupported and unpopular product.

When support is dropped from enterprise products, continued development of the filesystems is pointless because their main target audience was and still are enterprises. When the filesystems are no longer actively developed and supported, support in desktop products will be eventually dropped as well.

In the end all we have left is ext3, ext4, ReiserFS and Reiser4. ZFS is unlikely to gain any popularity because it is licensed under CDDL which makes it incompatible with GPL. And the ZFS filesystem is fairly young, taking many years for it to mature.

I don't personally like ext3/4 and ReiserFS/4 that much, my personal favorite was and still is JFS. Which makes this a very sad day to me.

Now you ask; since both JFS and XFS are licensed under GPL, what does it matter if these companies no longer develop it? Even until now most of the development have been done by the devs from IBM and SGI. This is unlikely to change because skilled enough developers to work on filesystems don't grow on trees and active development of a filesystem is a time-consuming job.

Even if the near future of both filesystems seems to be dark indeed, I hope there is a company or foundation out there which would take sincere interest in the matter, adopt the JFS/XFS developers and sponsor the projects.

---

### Post by argie on 2006-09-08
Ouch. I use XFS. What does this mean for me? I mean, does this really hurt current users in some way?

---

### Post by The Keeper on 2006-09-08
As far as I can tell, the current situation does not have much impact in short-term, but in long-term it means that quality of the filesystems will suffer due to lack of contributing developers. Bugs may not get fixed, compatibility problems may not get fixed, features may not be improved, new features may not be added, etc.

---

### Post by jdong on 2006-09-08
Well, the key issue here is, XFS and JFS are complex in nature, both in design and implementation aspects... Even if it's open source, if there's not that many people who understand how they work outside of their supporters (IBM/SGI), they will run the risk of becoming more or less abandoned in terms of bugfixes/improvements.

Sadly, it does seem like we're down to ext3/4 (Redhat + most of the Linux world), reiserfs3 (Novell/SuSE), reiser4 (Namesys/Linspire) as the big players for the future. They still have people around who know how it works and how to keep it maintained. I kind of worry about reiser4 though, because it would appear like from past history that once Namesys finds something newer and shinier (reiser4.1, reiser5 even?), they tend to abandon their previous products.

---

### Post by The Keeper on 2006-09-09
Indeed, which is why I wish there would be a company or foundation out there taking sincere interest in the matter and would hire the core filesystem developer teams from IBM and SGI and fund the projects, or at least one of them. These filesystems are just too good to just die off until something technically better and yet mature comes along.

I don't know any such companies or foundations but Canonical, so I decided to give it a shot and emailed Canonical yesterday and explained the situation.

I'm just daydreaming here, but it would be great if Canonical would hire the JFS and XFS core developer teams and aim JFS development primarily for desktops and notebooks and XFS development primarily for high-end workstations and servers.

Oh well, it is unlikely they would hire both teams even if they take interest in the situation, but I can always hope...

---

### Post by jdong on 2006-09-09
The general feeling I get from talking to Canonical developers is that they are absolutely devoted ext3 advocates and will not dare to poke with a 12-foot pole any other filesystem.

---

### Post by maniacmusician on 2006-09-09
ah what a bummer. it's starting to get outdated...

---

### Post by jdong on 2006-09-09
Well, I hope with all the big-name support behind ext3, they'll do something to bring the filesystem back up to the competition's standard...

To be honest, I do like ext3. From all of my experience, and from the experience of long-time Linux server/cluster administrators that I've talked to, ext3 is hands-down the most stable/reliable filesystem. However, I've snagged into ext3 limitations before, and as a result I'm using another filesystem (reiserfs at the moment, though I'm not 100% happy about it)

---

### Post by maniacmusician on 2006-09-09
yeah, its definitely stable. But it takes a bunch of tweaks to get it running fast enough, and that can be a pain on multiple installations. even though I b*tch about it sometimes, i'm probably going to stick with whatever fs the ubuntu team chooses. I can't really afford data loss at all.

---

### Post by atrus123 on 2006-09-09
> **The Keeper said:**
> 
Today I had the pleasure of briefly chat with one of IBM's JFS developers. He said that IBM no longer had any interest to continue supporting and funding JFS development because the big player Red Hat only supports ext3, and that SuSe is planning to also drop JFS support from its enterprise products as well.

Wrong.  SuSE has not supported JFS for some time.  However, openSUSE 10.2 is going to again incorporate JFS, which means that SLED isn't far behind.

IBM might want to reconsider.

---

### Post by The Keeper on 2006-09-09
Businesses like to play along with the major players. Since Red Hat has maybe around 80% of linux server market share, unless RHEL supports JFS and XFS which are both designed for high-end workstations and servers it might not be strategically viable to put resources into developing JFS/XFS.

It is hard to persuade Red Hat to include support for JFS/XFS since they have invested considerable amount of resources to develop ext4, which is in my opinion stupid move because we have technically superior file systems GPL'ed right here and been around since 90's.

Nevertheless, it is good news if SuSe will have JFS/XFS support since as far as I know, SuSe is the second biggest player in the linux server market after Red Hat.

---

### Post by gnomeuser on 2006-09-09
Both SuSE and Fedora have unofficial support for XFS and JFS just pass the relevant options to the installer. That is not likely to change. I also believe Ubuntu installs on XFS and JFS, if there are enough users to warrent official support it will happen.

Personally I'm a huge Reiser4 advocate, it seems like the way forward and now with the "plugins" to help them add functionality without having to throw away big piles of code there is very little chance of the FUD scenerio of them leaving the 4.x series behind. And wait.. yes Namesys are still supporting ReiserFS v3 the only thing they don't do is add features which is a good thing from stability. SuSE have added xattr support to ReiserFS in the kernel and it caused all kinds of horror because bolting new technology on age old designs that aren't as flexible as they could or should be (and Reiser4 is the correct design solution now and for the forseeable future) is catagorically a bad idea.

---

### Post by The Keeper on 2006-09-09
Fedora and RHEL are different products though and businesses will almost always choose RHEL over Fedora. There's a reason why RHEL has majority of the server market share. The problem here seems to be RHEL more than anything else.

---

### Post by jdong on 2006-09-09
> **The Keeper said:**
> It is hard to persuade Red Hat to include support for JFS/XFS since they have invested considerable amount of resources to develop ext4, which is in my opinion stupid move because we have technically superior file systems GPL'ed right here and been around since 90's.

The only thing is, the filesystem consistency techniques employed by XFS/JFS all assume a level of hardware reliability (i.e. battery backed up write cache, unexpected voltage drop does not cause garbage to leak to the disks, etc) that is simply not true on average x86 hardware... ext3 as a result is a lot more dependable on cheap x86 hardware compared to the other filesystems. Until the other filesystems get some degree of protection against unreliable hardware, I don't feel safe employing them on the average system. And, XFS did get write barriers starting with 2.6.17, but in some real-world situations (i.e. copying a kernel source tree) I've noticed a significant (100-150%) drop in performance, which is slightly concerning.

---

### Post by The Keeper on 2006-09-10
In my experience and knowledge that is not so true with JFS, which is why I prefer it over XFS. The main selling point of ext3 is its popularity and proven reliability. JFS is unpopular and its reliability is largely unproven. However, from my experience I would go as far as to say that ext3 is more reliable only if you enable full data journaling.

---

### Post by jdong on 2006-09-10
JFS does not employ an ordered journaling technique that reiserfs and ext3 support, which means after an abrupt shutdown you are more likely to end up with files that are half-old and half-new.

The developers of JFS on their mailing list have expressed that they are interested in writing an ordered journaling mode, but have not done so.

---

### Post by articpenguin on 2008-02-06
JFS is still supported,but not full time. It has a maintainer working on it part time.

---

### Post by bpny on 2008-02-06
Oracle is working on Brtfs for linux, [http://oss.oracle.com/projects/btrfs/]("http://oss.oracle.com/projects/btrfs/")  Looks very nice.

---

### Post by phrostbyte on 2008-02-06
EXT4 is still in development, and it might turn out to be a really good FS, that Ubuntu will probably pick up as default at some point.

---

### Post by regomodo on 2008-02-06
Thats rubbish news for me. I won't use anything but XFS (plus ext2 for /boot).

However, is XFS that buggy? I've used it for a while and have not had any problems yet :bites lip:

---

### Post by regomodo on 2008-02-06
> **bpny said:**
> Oracle is working on Brtfs for linux, [http://oss.oracle.com/projects/btrfs/]("http://oss.oracle.com/projects/btrfs/")  Looks very nice.

cheers for that link. Never heard of it and it appears to be good according to their data

---

### Post by Sunflower1970 on 2008-02-06
Well, poo. I just switched my / FS to JFS...I won't be changing any time soon though. I find it makes things just a tad snappier on my old system.

---

### Post by jrusso2 on 2008-02-06
I have been using JFS for my / for a long time now and never had a problem.  Used Resier and XFS in the past too and never had a problem.

In fact the only problems I have had with data or file system loss has been with ext2 and ext3.

The people that I know that have had issues have all been with ext 3.

I really don't know why people think its so reliable.

---

### Post by SunnyRabbiera on 2008-02-06
But both projects are under the GPl, they just need some thinkers to make the work continue.

---

### Post by 20thCenturyBoy on 2008-02-06
> **SunnyRabbiera said:**
> But both projects are under the GPl, they just need some thinkers to make the work continue.

The problem is most tinkerers aren't able to work on file system development either because they don't have enough time for such a massive product or they just don't understand how to.

I'm extremely interested in ZFS at the moment. I hope to see it gain popularity in the (near) future.

I never used JFS or XFS so I really have no opinion on the support drop. But I''m sad to see some options taken away if that's the result.

---

### Post by SunnyRabbiera on 2008-02-06
> **20thCenturyBoy said:**
> The problem is most tinkerers aren't able to work on file system development either because they don't have enough time for such a massive product or they just don't understand how to.

I'm extremely interested in ZFS at the moment. I hope to see it gain popularity in the (near) future.

I never used JFS or XFS so I really have no opinion on the support drop. But I''m sad to see some options taken away if that's the result.

yeh but if its one thing I have learnd is that with linux there is always something going on.
ZFS might take over though, if it was ever GPL'ed.
That might be soon of course.

---

### Post by The Keeper on 2008-02-07
WoW! Almost 1.5 years old thread of mine got suddenly revived. :D

And thanks for letting us know about Btrfs. It seems fairly new project so it'll be very long time before we'll be seeing it available in any mainstream distro.

---

### Post by slimdog360 on 2008-02-07
oh well

---

### Post by articpenguin on 2008-02-07
it should be 

The beginning of an end of Reiserfs & XFS

Reiserfs is dead with hans in jail and namesys always being down.

---

### Post by oomingmak on 2008-02-07
> **bpny said:**
> Oracle is working on Brtfs for linux, [http://oss.oracle.com/projects/btrfs/](http://oss.oracle.com/projects/btrfs/)  Looks very nice.
Yes, that's the kind of FS that interests me (along with ZFS).. 

I hate Ext 2/3/4.

---

### Post by articpenguin on 2008-02-07
> **oomingmak said:**
> Yes, that's the kind of FS that interests me (along with ZFS).. 

I hate Ext 2/3/4.

I hate them to. 

they should stop making the ext* filesystems backward compatible and make a new filesystem from scratch like Btrfs.

---

### Post by leftorvo on 2008-02-07
I hope nothing happens to it. I use XFS.

---

### Post by bpny on 2008-02-07
Here is some more info on Brtfs [http://kerneltrap.org/Linux/Btrfs_0.12_Performance_Improvements]("http://kerneltrap.org/Linux/Btrfs_0.12_Performance_Improvements")  I can't wait wait for the day this go into the mainline kernel and use this on my Ubuntu servers.

---

### Post by zekopeko on 2008-02-07
> **articpenguin said:**
> I hate them to. 

they should stop making the ext* filesystems backward compatible and make a new filesystem from scratch like Btrfs.

i can't wait when thousands of admins find this post and ask you what should they do with their 20+ TB ext3 filesystems when converting to this new uber cool non-backward compatible fs.

---

### Post by roachk71 on 2008-02-07
Although it's sad to hear about the support drop for JFS and XFS, both (at least in my humble opinion) are more stable and efficient on this computer.

Ext3 always ended up fixing errors and losing data after file system checks, so I use Ext2 for my boot and root partitions. 

And even though it doesn't take power failures all that well, I still use XFS for /usr, /var and /home, due to its speed, efficiency and security. So I hope Ubuntu keeps the option for using this file system.

---

### Post by articpenguin on 2008-02-08
they still have reiserfs and its umaintained =)

---

### Post by roachk71 on 2008-02-08
A bit of advice regarding ReiserFS:

 Be careful using version 3 of ReiserFS on Samsung hard disks; some have an LBA48 controller glitch that can lead to data and file system corruption (at least that's happened on my old notebook.) That machine had a brand-new 120GB HM120JC model before it failed. The new computer came with an SP2504C from the same manufacturer, so I'm reluctant to try that FS again...

---

### Post by BOBSONATOR on 2008-02-08
Reiser FTW! i have a 10 gig partition for arch, and its quick!

---

### Post by kevdog on 2008-02-08
> **BOBSONATOR said:**
> Reiser FTW! i have a 10 gig partition for arch, and its quick!

How quick??  I mean are we talking like a 1 second differential in random access times here?  Just wondering if we are comparing milliseconds here.

---

### Post by Polygon on 2008-02-08
> **zekopeko said:**
> i can't wait when thousands of admins find this post and ask you what should they do with their 20+ TB ext3 filesystems when converting to this new uber cool non-backward compatible fs.

so true.

---

### Post by traxxas on 2008-02-11
> **zekopeko said:**
> i can't wait when thousands of admins find this post and ask you what should they do with their 20+ TB ext3 filesystems when converting to this new uber cool non-backward compatible fs.

They will do what every other admin with half a brain would do, modprobe ext3.  If you break backwards compatibility you leave a path to access the older data, it will just not have the features available in the new fs. 

Back on topic, my problem with ext3 is on a laptop hard drive it makes me feel like I'm using 2 generations older of hardware.  The main thing they should be addressing in ext4 is getting it as fast as xfs/jfs/reiser.

---

### Post by ch_123 on 2008-02-11
Doesnt IBM still use JFS for its commercial UNIX variants? Therefore, wouldnt development continue on it in some form?

---

### Post by articpenguin on 2008-02-11
IBM does not maintain the JFS version for linux. It maintains the JFS version for AIX.

---

