---
title: "Is there software that work like &quot;SuperCache&quot; on Windows Server?"
date: 2009-10-25
forum: Server Platforms
---

### Post by SuperMENG on 2009-10-25
I want to build linux file server that working so hard.
20 client request several files amount 10-500MB in same time.
so I have ever heard that software name "SuperCache" on Windows Server
that will store the frequently using files in RAM for faster reading than HARDDISK.
 
thank you..

---

### Post by scorp123 on 2009-10-25
Linux already does that automatically. LOL, but nice to know that Windows is catching up.

---

### Post by SuperMENG on 2009-11-05
So, how do I config "amount of ram" we use for this thing?

---

### Post by Lars Noodén on 2009-11-07
The more I hear about Windows the more shocked I am at the normal things it can't do.  8(  

> **SuperMENG said:**
> So, how do I config "amount of ram" we use for this thing?

The short answer (contingent on the guess of EXT being correct) is to use 'tune2fs'.  Also, the package 'systat' has a lot of performance monitoring tools that can show utilization and bottlenecks.  

The long answers is that it depends on the filesystem.  You have a choice of HFS, EXT2, EXT3, EXT4, Reiser, XFS, JFS, SMB, AFS, NFS, Btrfs.  The choices are there because they do different things and because the goal of Linux is to help you do different things.  There a load of others that won't be of use to you in this context,  but help get the idea of what a filesystem is and is for, GoogleFS and Hammer are two interesting ones from that category.  

If you did not choose any particular filesystem on purpose, then you probably have one of the EXT's.  [gparted](http://manpages.ubuntu.com/manpages/karmic/en/man8/gparted.8.html), [parted](http://manpages.ubuntu.com/manpages/karmic/en/man8/parted.8.html) or even [mount](http://manpages.ubuntu.com/manpages/karmic/en/man8/mount.8.html) or df will show which ones are in use on your machine.

Here is a comparison of four:
[http://www.linux-mag.com/cache/7497/1.html](http://www.linux-mag.com/cache/7497/1.html)

JFS might be worth looking at.
EXT might be fine, too.

You can tune any of them based on your needs.  Some of the simplest refinements include whether you have lots of small, medium or large files and whether these are written a lot or read a lot.

---

### Post by Lars Noodén on 2009-11-07
FYI:

[indent][i]"Linux automatically uses all free RAM for buffer cache, but also automatically makes the cache smaller when programs need more memory"
[/i]
*The Linux System Administrator's Guide*.   [7.6. The buffer cache](http://www.faqs.org/docs/linux_admin/buffer-cache.html)  ( 2008 )[/indent]



[Anatomy of the Linux file system](http://www.ibm.com/developerworks/linux/library/l-linux-filesystem/#N10113), an introductory overview.

---

### Post by SuperMENG on 2009-11-07
thank you very much... :)

---

