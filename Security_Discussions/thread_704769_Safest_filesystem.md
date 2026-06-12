---
title: "Safest filesystem"
date: 2008-02-22
forum: Security Discussions
---

### Post by frodemt on 2008-02-22
What is the safest filesystem I can choose when I comes to safety against filesystem corruption? I cant say I like that EXT3 dont support realtime integrity check.

---

### Post by p_quarles on 2008-02-23
The safest filesystem is one that is backed up. Ext3 and other journaled systems are relatively good at fighting/correcting corruption, but no filesystem will protect you from a hard drive failure.

---

### Post by astrotech226 on 2008-02-23
I've had great luck with ext3, reiser and jfs for different applications.  It really depends on what you are trying to do.  Each has strengths and are good at some things and not others.

What do you want the filesystem for?  File storage, database, etc...?

---

### Post by frodemt on 2008-02-24
I would say general use for mye primary disk.

Other disk must store files long term. These files will not be modified.

---

### Post by tubezninja on 2008-02-24
For the purposes you state, ext3 should be fine, really.

The only *nix file system I've seen that lets you do live integrity checking is HFS+ for the Mac.  But, I wouldn't call it a **true** *nix filesystem, and even it is hit or miss when mounted.

---

### Post by astrotech226 on 2008-02-25
> **frodemt said:**
> I would say general use for mye primary disk.

Other disk must store files long term. These files will not be modified.

I would stick with ext3.  It's probably the more "well rounded" of the filesystems if you want this partition for general use.  Ext3 has never let me down yet and I've seen numerous power outages/generator problems that have unexpectedly shutdown racks of equipment.

---

### Post by frodemt on 2008-02-25
> **scaredpoet said:**
> For the purposes you state, ext3 should be fine, really.

The only *nix file system I've seen that lets you do live integrity checking is HFS+ for the Mac.  But, I wouldn't call it a **true** *nix filesystem, and even it is hit or miss when mounted.

I did not understand the thing about hit or miss when mounted. Could you explain? :)

---

### Post by frodemt on 2008-02-25
> **astrotech226 said:**
> I would stick with ext3.  It's probably the more "well rounded" of the filesystems if you want this partition for general use.  Ext3 has never let me down yet and I've seen numerous power outages/generator problems that have unexpectedly shutdown racks of equipment.

You use EXT3 on server?

---

### Post by astrotech226 on 2008-02-25
> **frodemt said:**
> You use EXT3 on server?

I do for my file storage server with access control lists.  I like Reiser where there are going to be thousands and thousands of files that will come and go quickly, like for imap email.  They delete really fast.

I've read that jfs is good for database file systems.

But for multipurpose use, I always use ext3.  Even for my personal machines.

---

### Post by articpenguin on 2008-02-25
Reiserfs/xfs more prone to corruption as they do logical journalling

theodore tso explains why [http://zork.net/~nick/mail/why-reiserfs-is-teh-sukc](http://zork.net/~nick/mail/why-reiserfs-is-teh-sukc)

JFS has never corrupted on me. 

ext3 is just ext2 with a journal.

---

### Post by astrotech226 on 2008-02-25
> Reiserfs/xfs more prone to corruption as they do logical journalling

I can vouch for the xfs problems.  I tried it on a laptop once to get a little extra performace and one out of ten clean shutdowns, it would trash my Thunderbird profile.  Most likely because of the zeroing the open files issue discussed in the link you posted.

Never had the problem with Reiser, but I also don't trust it as much as ext3.  I use it for email because I'm on clean and generated power on a large APC Symmetra and the data itself is kept on a SAN of multiple modules.

If it was a server on my desk, it would most definitely be ext3.

---

