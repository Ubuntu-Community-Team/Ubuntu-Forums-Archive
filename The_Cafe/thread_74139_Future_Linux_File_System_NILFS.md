---
title: "Future Linux File System NILFS?"
date: 2005-10-11
forum: The Cafe
---

### Post by Turk on 2005-10-11
NILFS is a log-structured file system developed for the Linux kernel 2.6. NILFS is an abbreviation of the New Implementation of a Log-structured File System. A log-structured file system has the characteristic that all file system data including metadata is written in a log-like format. Data is never overwritten, only appended in this file system. This greatly improves performance because there is little overhead regarding disk seeks. NILFS also has the following specific features:

    * Slick snapshots.
    * B-tree based file and inode management.
    * Immediate recovery after system crash.
    * 64-bit data structures; support many files, large files and disks.
    * Loadable kernel module; no recompilation of the kernel is required.
[http://nilfs.sourceforge.net/](http://nilfs.sourceforge.net/)

What do you think about this fs? It's in BETA, will it be used for Ubuntu 6.1 maybe?

---

### Post by Wolki on 2005-10-11
[QUOTE=Turk]What do you think about this fs? It's in BETA, will it be used for Ubuntu 6.1 maybe?[/QUOTE]

There is no 6.1 (probably), since ubuntu versions are named after their release date, and they are released in April and October. But I doubt it will be in Dapper (6.04), unless it makes it into the stable kernel by then. Usually filesystems are added slowly and tested very well, since a malfunctioning file system has all sorts of negative effects (like losing all your data).

---

### Post by nocturn on 2005-10-11
I don't know, but it looks a lot like reiserfs and that has been arround for a while and has proven very stable.

---

### Post by ewr2san on 2007-12-14
Anyone re-thingking about this?  The Nov Builds of NILFS seem much improved.  Very fast!

---

### Post by mips on 2007-12-14
Pity we can't have ZFS though.

---

### Post by Dimitriid on 2007-12-14
> * Loadable kernel module; no recompilation of the kernel is required.

Thats impressive.

---

### Post by ewr2san on 2007-12-14
Well, IMHO where ZFS shines is when you have many Hard Drives in a strorage pool.  It's in the server space where it's best.

NILFS has continious snapshots, so you can do things very much like apple's "Time Machine" and revert files, etc... Very slick on a single Hard disk (or more).  NILFS could be very nice in ubuntu desktop.

---

### Post by foxmulder881 on 2007-12-14
I'd like to see both ZFS and NILFS implemented into Ubuntu eventually.
But only when both have been fully tested and finalized and claimed as 'safe' to use by the Ubuntu development team.

One of the main reasons I like using Linux is because of the vast choice of file systems you have to choose from.
Currently, I use ReiserFS.
It's all about "choice".

---

### Post by SunnyRabbiera on 2007-12-14
> **nocturn said:**
> I don't know, but it looks a lot like reiserfs and that has been arround for a while and has proven very stable.

Yeh its a KILLER filesystem :p

---

### Post by hanzomon4 on 2007-12-14
Can you boot from ReiserFS? And is it safe for sudden power outages? I screwed my self by using xfs for both / and /home, now I have to much data to move to another hard drive.

---

### Post by maniacmusician on 2007-12-14
> **SunnyRabbiera said:**
> Yeh its a KILLER filesystem :p

:rolleyes:

---

### Post by foxmulder881 on 2007-12-14
> **hanzomon4 said:**
> Can you boot from ReiserFS? And is it safe for sudden power outages? I screwed my self by using xfs for both / and /home, now I have to much data to move to another hard drive.

Well, I boot from it with no probs.
And you have to ask yourself, "Is any filesystem safe when you get a sudden power outage?". Really?!?

---

### Post by herbster on 2007-12-14
Damn, I thought the filesystem was called MILFs for a second.

---

### Post by yatt on 2007-12-14
> **foxmulder881 said:**
> Well, I boot from it with no probs.
And you have to ask yourself, "Is any filesystem safe when you get a sudden power outage?". Really?!?
XFS is actually really bad with power outages. IME, you will usually only lose your firefox config files during a power outage (whether FF is open or not). With XFS, you'll lose others like xorg.conf, fstab, mtab, etc.

XFS can't be used for /boot with the old style Grub(the one Ubuntu uses).

Anyways, I use JFS as it is almost as fast as XFS (not quite as good with huge files, but comparable elsewhere. I'd give NILFS a shot if I had a kernel with support for it, and the time to do a Gentoo....

---

### Post by hanzomon4 on 2007-12-15
Yeah I use jfs on root and xfs for home.

---

### Post by ewr2san on 2007-12-16
Reiser is a very good and fairly solid filesystem.. However there are some rather neat performance benefits to NILFS, as well as the contunious data protection features which allow you to roll back to any point in time.

Im told that Mac has a feature called "Time machine" which is similar.

---

### Post by spockrock on 2007-12-17
> **maniacmusician said:**
> :rolleyes:

LOL, I think you are :rolleyes: for the same reason I am when reading that post.

---

### Post by foxmulder881 on 2007-12-20
> **spockrock said:**
> LOL, I think you are :rolleyes: for the same reason I am when reading that post.


For the readers who have no idea what these guys are referring to. Read here...

[http://tinyurl.com/zkv3n](http://tinyurl.com/zkv3n)

---

