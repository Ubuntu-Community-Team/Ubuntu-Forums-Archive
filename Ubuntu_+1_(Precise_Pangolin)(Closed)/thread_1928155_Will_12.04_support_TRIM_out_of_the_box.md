---
title: "Will 12.04 support TRIM out of the box?"
date: 2012-02-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ubuntukid on 2012-02-19
With Ubuntu 11.10 one has to add discard to the fstab file for automatic TRIM support. I was wondering if 12.04 will support SSD and TRIM out of the box, without the need to edit system files. I know its not difficult to edit it, but seeing as SSDs are becoming much more normal, I would think it would make sense to support this, especially in an LTS release which will be around for quite some time.

---

### Post by MacUntu on 2012-02-19
You can subscribe to this bug report: [https://bugs.launchpad.net/ubiquity/+bug/867794](https://bugs.launchpad.net/ubiquity/+bug/867794)

---

### Post by fjgaude on 2012-02-19
Well, it's not too hard to fix this apparently low priority bug.

In a terminal, after you have installed an OS onto your SSD, go into the file /etc/fstab with an editor, gedit, and make the drive line look something like this:

```
UUID=d65e4ad3-6315-4838-97a1-ec574cb8575f / ext4 noatime,nodiratime,discard,errors=remount-ro                             0       1
```

The only thing you really have to do is to add the word "discard," to the line. This must be done when you are in root, like:

```
sudo gedit /etc/fstab
```

You can add the other items, noatime, and nodirtime, if you wish to reduce the writes to the SSD.

Let us know how you make out. Thanks!

---

### Post by ubuntukid on 2012-02-19
> **fjgaude said:**
> Well, it's not too hard to fix this apparently low priority bug.

In a terminal, after you have installed an OS onto your SSD, go into the file /etc/fstab with an editor, gedit, and make the drive line look something like this:

```
UUID=d65e4ad3-6315-4838-97a1-ec574cb8575f / ext4 noatime,nodiratime,discard,errors=remount-ro                             0       1
```

The only thing you really have to do is to add the word "discard," to the line. This must be done when you are in root, like:

```
sudo gedit /etc/fstab
```

You can add the other items, noatime, and nodirtime, if you wish to reduce the writes to the SSD.

Let us know how you make out. Thanks!

I did this, and also found a way to test if trim is active, and it seems to be working. Maybe its just my imagination, but my computer does seem faster now after reboot. Been running ubuntu on my SSD without TRIM for about a month and a half up untill now.

---

### Post by fjgaude on 2012-02-19
I think TRIM takes some time to do its job, to get things up to speed again. Glad you got things going. The SSD should last five or more years, at least that's what I'm told.

---

### Post by ubuntukid on 2012-02-19
> **fjgaude said:**
> The SSD should last five or more years, at least that's what I'm told.

This is one of the reasons why I wonder if 12.04 shouldn't enable trim by default if it detects an ssd. Laptops with ssd are starting to become more regular (ultrabooks for example) and if an average user buys an ultrabook and installs ubuntu on it, I doubt they will have enough knowledge to know what trim is and that they need to activate it, which could potentially shorten the lifetime of their hardware.

---

### Post by fjgaude on 2012-02-19
You are so right... the programmers seem to have a full plate these days with lots of things they don't get around to fixing. So be it. Ubuntu is not for everyone, yet. <smile>

---

### Post by dcstar on 2012-02-20
> **ubuntukid said:**
> This is one of the reasons why I wonder if 12.04 shouldn't enable trim by default if it detects an ssd. Laptops with ssd are starting to become more regular (ultrabooks for example) and if an average user buys an ultrabook and installs ubuntu on it, I doubt they will have enough knowledge to know what trim is and that they need to activate it, which could potentially shorten the lifetime of their hardware.

Since the Linux kernel has (supposedly) been able to detect rotational and non-rotational drives for years now, it is surprising that EXTx partitions created on non-rotational devices do not have this set by default.

My understanding is that TRIM is currently at partition level in Linux, so if you have multiple partitions on your SSD device that are **not** Trim supported then they may use up **all** of your empty SSD blocks and never, ever release them for reuse.

The bottom-line seems to be that **all** of your partitions on a Linux SSD should be EXTx (or whatever else supports TRIM in Linux) otherwise you could virtually have a no-TRIM drive after some time.

---

### Post by eyelessfade on 2012-02-20
> **fjgaude said:**
> 
You can add the other items, noatime, and nodirtime

Not that it matters but noatime is a superset of nodirtime. You don't need to set both.

---

### Post by ubuntukid on 2012-02-20
I found this interesting forum post for those interested in ssd performance on Linux,

[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

---

### Post by fjgaude on 2012-02-20
> **ubuntukid said:**
> I found this interesting forum post for those interested in ssd performance on Linux,

[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

Yes...

```
frank@cutie:~$ sudo hdparm -I /dev/sdb | grep TRIM
	   *	Data Set Management TRIM supported (limit 1 block)
	   *	Deterministic read data after TRIM
```

I don't have but one partition on the SSD, bootable.

---

### Post by dcstar on 2012-02-25
> **MacUntu said:**
> You can subscribe to this bug report: [https://bugs.launchpad.net/ubiquity/+bug/867794](https://bugs.launchpad.net/ubiquity/+bug/867794)

I have added a comment to this bug report on how to detect if a drive is actually a SSD, so someone may want to write a script to automatically test this and then add the "discard" option to the relevant /etc/fstab line.

I'm sure a lot of people would appreciate this sort of thing (at least until it is added automatically by the relevant Linux tools).

---

### Post by MacUntu on 2012-02-25
It's not that they don't know how to detect the SSD, it's that the 'discard' feature wasn't ready enough to become default at that time. This should be re-evaluated since a lot of users are using it for quite some time now, and I've yet to hear of any problems.

Apart from that: missing TRIM support is not such a big deal for current-gen SSD drives anymore (at least that's what I've read about OCZ and Crucial drives).

---

### Post by philhughes on 2012-02-25
There's a school of thought that adding discard to fstab is a bad idea, and instead fstrim should be run on a regular basis:

[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

---

### Post by nrundy on 2012-02-25
> **MacUntu said:**
> 

Apart from that: missing TRIM support is not such a big deal for current-gen SSD drives anymore (at least that's what I've read about OCZ and Crucial drives).

Intel SSD drives without TRIM are a disaster. It's very much needed if you have Intel drive.

---

### Post by pressureman on 2012-02-25
> **philhughes said:**
> There's a school of thought that adding discard to fstab is a bad idea, and instead fstrim should be run on a regular basis:

[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

+1

Enabling discard/trim will impact write operations, and if you work with git/svn/whatever checkouts a lot, all those tiny little files being frequently updated will suffer in performance.

A daily/weekly cron entry to run `fstrim /dev/sda1` would be my preference.

---

### Post by nrundy on 2012-02-25
> **pressureman said:**
> 

A daily/weekly cron entry to run `fstrim /dev/sda1` would be my preference.

How exactly does one set this daily/weekly thing up?

Sounds like the reason Discard is not added by default is that it is not proven to effectively work.

---

### Post by fjgaude on 2012-02-25
> **nrundy said:**
> Intel SSD drives without TRIM are a disaster. It's very much needed if you have Intel drive.

Intel SSDs, is that because until model 520 they didn't use the Sandforce controllers?

---

### Post by pressureman on 2012-02-26
> **nrundy said:**
> How exactly does one set this daily/weekly thing up?

Sounds like the reason Discard is not added by default is that it is not proven to effectively work.

Just create an executable file (chmod +x) with the following contents:

```

fstrim /

```

and move that to /etc/cron.daily or /etc/cron.weekly directory, depending on your preference.

Note that the argument specified to fstrim is a mountpoint, not a device name (as I mistakenly implied in an earlier post). If you have multiple partitions on your SSD, specify the fstrim command for each mountpoint that you have.

---

### Post by dcstar on 2012-03-01
> **pressureman said:**
> 
..........
Note that the argument specified to fstrim is a mountpoint, not a device name (as I mistakenly implied in an earlier post). If you have multiple partitions on your SSD, specify the fstrim command for each mountpoint that you have.

The whole point of TRIM is to let the SSD hardware know when the OS is no longer using a logical block on the partition. Then the SSD can go through the process of erasing the block and placing it back in the pool for reuse. Whether this is done "on the fly" using the DISCARD option on a filesystem that supports it or is done in a batch later on is the choice you have.

If you have a system that is doing so many writes that DISCARD performance impacts becomes noticeable, then I would suggest that the SSD would be consuming spare blocks at a high rate and waiting to clear them with a batch may be problematic.

Until they make SSDs that don't have the big block reuse penalty when all the spare blocks are used up then one of these methods must be used.

---

### Post by andrewabc on 2012-03-01
Ubuntu still doesn't support TRIM with default install (without having to edit config files etc)!?!?!?

I've been asking for this since [September 2009](http://ubuntuforums.org/showthread.php?t=1262302) and every [subsequent](http://ubuntuforums.org/showthread.php?t=1865253) ubuntu release since [then](http://ubuntuforums.org/showthread.php?p=10601450#post10601450).

I've given up on this. The fact that they had 3 years to get something extremely important done, and havn't for a LTS (the second LTS that hasn't had TRIM by default).

B-b-but the kernel supports trim! I thought linux was cool when it supported trim before windows, and yet 3 years later win7 (which I now use) enables trim with an install and ubuntu doesn't. Canonical more worried about changing things around every release than something as simple as trim. Sigh.

I assume ubuntu properly aligns SSD (with correct block/page size)? It didn't back in 2009, and I forget if they updated that (I think they did).

Sorry for the rant. Also expect in 6 months time for the same thread to be created for next release.

---

### Post by CrByte on 2012-03-01
Your joking right about Ubuntu does not come with TRIM out of the box?

I am one that does not like touching system config files and as SSDs become used more and more, this in important to have.

I am starting to think again about making ubuntu the default OS on my desktop with an SSD.

If I do end up installing it on my desktop when 12.04 hits stable what would be best editing /etc/fstab adding discard or running `fstrim /dev/sda1` every once and awhile?

I really can not see why there is no out-of-box TRIM support in in ether method a cron that runs fstrim once a day or using discard

---

### Post by effenberg0x0 on 2012-03-01
> **CrByte said:**
> Your joking right about Ubuntu does not come with TRIM out of the box?

I am one that does not like touching system config files and as SSDs become used more and more, this in important to have.

In Linux, we're past the point of "use trim or everyone will die" discussion. The real benefit vs impact and the best way to do it is what is currently under discussion. This is file system and kernel, not in the real of applications. This is a professional Operating System - nothing is done simply because non-technical individuals think it's best. Everything goes through a decision process, in which individuals with the capacity to have an opinion (developers) decide. 
> **CrByte said:**
> 
I am starting to think again about making ubuntu the default OS on my desktop with an SSD.
If I do end up installing it on my desktop when 12.04 hits stable what would be best editing /etc/fstab adding discard or running `fstrim /dev/sda1` every once and awhile?
I really can not see why there is no out-of-box TRIM support in in ether method a cron that runs fstrim once a day or using discard
If you have good enough technical arguments proving that one way is better than the other, maybe some test cases, and you share them with others, there's great chance the next release will be exactly the way you want it to regarding TRIM. The problem is, no one seems to have really solid, reliable arguments and proofs right now. Some say it makes sense, others say it's unnecessary. 

But gladly this is Linux: A system used by individuals with technical curiosity and superior IT skills, motivated to learn and try new things, which allows for an enormous degree of customization and encourages its users to do them. Enabling any discard method won't take a user more than 10 to 20 seconds if he types slow, until there's no consensus.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-03-01
> **andrewabc said:**
> Ubuntu still doesn't support TRIM with default install (without having to edit config files etc)!?!?!?

I've been asking for this since [September 2009]("http://ubuntuforums.org/showthread.php?t=1262302") and every [subsequent]("http://ubuntuforums.org/showthread.php?t=1865253") ubuntu release since [then]("http://ubuntuforums.org/showthread.php?p=10601450#post10601450").

I've given up on this. The fact that they had 3 years to get something extremely important done, and havn't for a LTS (the second LTS that hasn't had TRIM by default).

B-b-but the kernel supports trim! I thought linux was cool when it supported trim before windows, and yet 3 years later win7 (which I now use) enables trim with an install and ubuntu doesn't. Canonical more worried about changing things around every release than something as simple as trim. Sigh.

I assume ubuntu properly aligns SSD (with correct block/page size)? It didn't back in 2009, and I forget if they updated that (I think they did).

Sorry for the rant. Also expect in 6 months time for the same thread to be created for next release.

It does align correctly and supports discard.
I appreciate the fact that, given that you can activate discard in 10 seconds in your PC, you seem to be genuinely concerned about the PCs of others since 2009. That's very noble.

Regards,
Effenberg

---

### Post by andrewabc on 2012-03-02
> **effenberg0x0 said:**
> The real benefit vs impact and the best way to do it is what is currently under discussion. 

It's been known since 2009 that there is a real benefit, and in some cases is required to make an actual SSD fast. An SSD can have performance severely hindered ([70+% loss in performance](http://www.anandtech.com/show/2829/9)) if it has no TRIM.

With no TRIM by default in 12.04 which is going to be supported for 3(?) years, they'll be screwing any SSD owner that is not technically inclined enough to know about TRIM and to config files. They'd reasonably assume it would work by default. There should be a big warning when installing ubuntu to an SSD that trim is not enabled by default and a link to website on how to enable it.

Ubuntu: *Linux for humans*, I think not.

Even a new SSD drive that is very popular and probably best has poor non trim performance.
[The Crucial m4 (Micron C400) SSD Review](http://www.anandtech.com/show/4253/the-crucial-m4-micron-c400-ssd-review/2)
It goes from 240mb/s write to 20mb/s.

This makes ubuntu look really bad, and can't be recommended to anyone wanting to use an SSD unless they want to edit fstab, and I have horror stories of trying to edit that config file (disappearing drives etc).

---

