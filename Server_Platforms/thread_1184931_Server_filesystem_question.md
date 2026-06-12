---
title: "Server filesystem question"
date: 2009-06-11
forum: Server Platforms
---

### Post by Krupski on 2009-06-11
Hi all,

I'm running a file server box with Ubuntu 9.04 server, 64 bit, 8 gigs of ram and three 1TB hard drives setup as a 2TB RAID-5 array.

I've found that if I use the XFS filesystem instead of the EXT3 filesystem, the throughput (disk read/write speed) almost doubles from 30-some megabytes/sec to 60-some megabytes per second.

So, a red flag goes up in my head... "am I getting something for nothing"?

If XFS is so much faster, why does Ubuntu use EXT3/EXT4 by default?

If there's a REALLY good reason (like better data integrity or better ability to recover from a crash or whatever), then I would take the speed hit and use EXT3.

I mean... XFS has been around for a long time... SGI uses it... it CAN'T be all that bad.

So, what's the reason that Ubuntu defaults to EXT3... and is there a really good reason why I should use EXT3 over XFS?

Thanks!

-- Roger

---

### Post by v3xtra on 2009-06-11
You should definitely do a bit of searching, there are tons of benchmark tests out there.  A quick google search showed me these tests:

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

[http://kevin.hatfieldfamilysite.com/?p=104](http://kevin.hatfieldfamilysite.com/?p=104)

[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

The last link, Wikipedia, states that > It is also considered safer than the other Linux file systems due to its relative simplicity and wider testing base. and > While in some contexts the lack of "modern" filesystem features such as dynamic inode allocation and extents could be considered a disadvantage, in terms of recoverability this gives ext3 a significant advantage over file systems with those features. The file system metadata is all in fixed, well-known locations, and there is some redundancy inherent in the data structures that may allow ext2 and ext3 to be recoverable in the face of significant data corruption, where tree-based file systems may not be recoverable.

So it seems as though EXT3 is safer because it is easier to recover information if it happens to be corrupt.  This may be why it is considered the "linux standard" of filesystems, but it would seem as though XFS is one of the best for file servers and servers in general.  Please read up on those topics and see which one seems to fit your purpose!

---

### Post by Polaris96 on 2009-06-11
XFS was originally designed for big statistical files on what used to be called supercomputers.  So, you're getting a fs that had a bunch of DARPA r&d and you're using it on big storage.  Basically, you're putting a square peg in the proverbial square hole.

Many MythTV types really like XFS for media storage HDDs.  If you're streaming media off your file server, I think you're using just about the best game in town.

I think you might find better seek times with ext or Reiser but I'm only guessing here.  The journaling functions of the more modern filesystems are most likely more sophisticated.  If the file sizes are relatively small, like many executables, then you're more concerned with access time than throughput, and a more sophisticated journaling system would be a big plus.  I'd probably use ext or reiser if I were running binaries (apps) off the drive and XFS for big statistical files.

---

### Post by HermanAB on 2009-06-11
Pretty much everything is faster than Ext3.  You will also get good results with IBM JFS.

---

### Post by scorp123 on 2009-06-12
> **HermanAB said:**
> You will also get good results with IBM JFS. Yeap ... I tested IBM JFS on a storage server once and I found it performs very very nice.

But honestly ... If you don't mind learning something new then go for OpenSolaris!! OpenSolaris feels very very much like a Linux system. You'd feel right at home. The real bonus of using OpenSolaris is this: You get ZFS. ZFS and its snapshot functions are soooo amazing. With OpenSolaris you also get a very nice GUI into GNOME ("Time Slider") so you can do all the snapshotting stuff right there in GNOME's Nautilus file manager:

[http://www.dslreports.com/forum/r22493596-OpenSolaris-200906-Time-Slider](http://www.dslreports.com/forum/r22493596-OpenSolaris-200906-Time-Slider)
[http://blogs.sun.com/erwann/entry/time_slider_screencast](http://blogs.sun.com/erwann/entry/time_slider_screencast)


If I have to or want to use Linux => I use XFS.
If I can use "something else" (e.g. because it's a server system and it won't really matter what the desktop will look like ...) => I'd go for OpenSolaris and ZFS

:)

---

### Post by dragos2 on 2009-06-29
My important servers run Raid ext3, and the rest JFS and XFS.

I have read about and documented, also run my own benchmarks and I can
tell that XFS is the fastest followed by JFS, use it only if you have UPS devices on production servers.

---

