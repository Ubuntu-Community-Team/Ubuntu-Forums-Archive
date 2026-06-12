---
title: "SUSE Dumping Reiserfs..."
date: 2006-09-16
forum: The Cafe
---

### Post by jdong on 2006-09-16
[http://www.suseforums.net/index.php?showtopic=24384&pid=131614&st=0entry131614](http://www.suseforums.net/index.php?showtopic=24384&pid=131614&st=0entry131614)

According to this thread over at SUSEforums, it appears like Novell/SUSE is going from reiserfs to ext3, also. They were the last major supporters of reiserfs.

So, what does this mean for the future of reiserfs? Will there continue to be people knowledgeable enough to maintain it in the kernel? Will it be labeled abandonware and taken out of the kernel?

---

### Post by TheRingmaster on 2006-09-16
the world may never know.

---

### Post by Lord Illidan on 2006-09-16
I dunno what to say... I switched to ext3 because it is easier to access in Windows..

Perhaps Reiser4 will be better, or ext4, or XFS...

---

### Post by Ramses de Norre on 2006-09-16
Or [ZFS]("http://www.sun.com/2004-0914/feature/"), currently being developped by Sun and looking very, very good.

---

### Post by BWF89 on 2006-09-16
> **Ramses de Norre said:**
> Or [ZFS]("http://www.sun.com/2004-0914/feature/"), currently being developped by Sun and looking very, very good.
The EXT line of filesystems have been use forever and is default on  most distros. It's gonna take something pretty incredible and alot of time for it to overtake EXT.

---

### Post by argie on 2006-09-16
Yikes, this seems to be the dying times for filesystems.

---

### Post by Rhapsody on 2006-09-16
> **Ramses de Norre said:**
> Or [ZFS]("http://www.sun.com/2004-0914/feature/"), currently being developped by Sun and looking very, very good.
Yes, but ZFS is licensed under the CDDL, which is incompatible with the GPL. That's going to make porting it to Linux harder. I don't think it'll stand a chance of competing with ext3 unless it's relicensed under a GPL-compatible license, no matter how good it is.

---

### Post by jdong on 2006-09-16
> **Rhapsody said:**
> Yes, but ZFS is licensed under the CDDL, which is incompatible with the GPL. That's going to make porting it to Linux harder. I don't think it'll stand a chance of competing with ext3 unless it's relicensed under a GPL-compatible license, no matter how good it is.

ZFS's OpenSolaris source code is licensed under the CDDL, but I don't see how that is anywhat relevant to a Linux port of ZFS. I doubt it would even be able to share any code with ZFS's OpenSolaris implementation.

For example, FreeBSD got a reimplementation of XFS in 7-CURRENT, under the BSD license, even though SGI's Linux implementation of XFS is GPL'd.



I will have to agree with SUSE for sticking with ext3 for now. That's where it seems like most of the Linux momentum is, and for now there still seems to be a promising future for ext3/4 with a smooth upgrade path (minus the herd of reiserfs users who have to migrate to ext3 via reformat).

In the long term, it's hard to speculate what will happen. Maybe ZFS will get adopted, or maybe OCFS2 will rock so much that we don't care much for ZFS anymore. But clearly today, SUSE has a dilemma to deal with, that none of the other filesystems can answer for, and ext3 is the best choice for today.

---

### Post by Virogenesis on 2006-09-16
ZFS is opensource but they have made it so it can only be included into one kernel and thats solaris now, it can be ran on linux but its got to be through userspace. 
Seems like we'll be using ext3 for everything now.

---

### Post by KaeseEs on 2006-09-17
I don't think we'll be using ext3 for everything just yet... I only use it for my boot partition, xfs for everything else.  JFS also has a good reputation for speed & reliability, and also uses little processor time.

As for SUSE, I think they made a good call if they really are going to transition from reiser... Hans' boys more or less abandoned it at merge and left its upkeep to other devs in order to work on reiser4, and if reiser4 ever gets into the mainline kernel, I don't doubt Namesys'll do the same again to work on reiser5.

---

### Post by kripkenstein on 2006-09-17
> **Rhapsody said:**
> Yes, but ZFS is licensed under the CDDL, which is incompatible with the GPL. That's going to make porting it to Linux harder. I don't think it'll stand a chance of competing with ext3 unless it's relicensed under a GPL-compatible license, no matter how good it is.

Yes, this is a major problem for ZFS on Linux. Unless ZFS is GPL'ed, it can't run as a Linux kernel module. It can (and I hear some work was done towards this) run in userspace under Linux - but this wouldn't be as fast as a kernel module.

Depending on the specifics of the CDDL (I am no expert), it may be possible to run ZFS on a BSD-based system, however. And it can certainly be run on an OpenSolaris kernel. There is already a version of Ubuntu using OpenSolaris instead of Linux as a kernel (Nexenta, GNU/Solaris), certainly a BSD one is possible (there is such a Debian system, I think). So, the open-source world, and Ubuntu in particular, may see ZFS in use at some point, in some way.

---

### Post by The Keeper on 2006-10-19
> **argie said:**
> Yikes, this seems to be the dying times for filesystems.

So true. With IBM working on ext4 and SGI being in serious financial troubles both JFS and XFS are dying as well. Now we've also had news of Reiser4 development troubles since Hans Reiser's arrest.

At this rate I would't be surpised if support for JFS, XFS, ReiserFS and Reiser4 would be dropped from mainline kernels alltogether. Which is a shame because even JFS and XFS are technically superior to ext4 if only they would support ordered journaling. *sigh* :(

---

### Post by Ubuntist on 2006-10-19
> **Lord Illidan said:**
> I dunno what to say... I switched to ext3 because it is easier to access in Windows..

How does ext3 make it easier to access Windows?

---

### Post by PriceChild on 2006-10-19
> **Ubuntist said:**
> How does ext3 make it easier to access Windows?[http://fs-driver.org](http://fs-driver.org)

---

### Post by Ubuntist on 2006-10-20
> **PriceChild said:**
> [http://fs-driver.org](http://fs-driver.org)

Thanks -- I wish I'd known about this before I chose to go with Reiser.  If I'm forced to dump Reiser at some point, this looks like a strong argument for switching to ext3.

---

