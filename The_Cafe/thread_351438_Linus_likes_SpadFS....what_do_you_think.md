---
title: "Linus likes SpadFS....what do you think?"
date: 2007-02-01
forum: The Cafe
---

### Post by RAV TUX on 2007-02-01
[http://artax.karlin.mff.cuni.cz/~mikulas/spadfs/](http://artax.karlin.mff.cuni.cz/~mikulas/spadfs/)
[http://freshmeat.net/projects/spadfslinux/?branch_id=67194&release_id=244299](http://freshmeat.net/projects/spadfslinux/?branch_id=67194&release_id=244299)
> 
 SpadFS is a new filesystem that I design and develop as my PhD thesis. It is an attempt to bring features of advanced filesystems (crash recovery, fast directories) and good performance without increasing code complexity too much. Uses crash counts instead of journaling (because journaling is too complex and bug-prone) and uses hash instead of btrees for directory organization.  Features: 
[LIST]
[*] New method to maintain consistency across crashes --- crash counts.
[*] 48-bit sector numbers. Supports device size up to 144PB.
[*] Variable block size from 512 bytes to machine page size. Due to design of Linux page cache, small blocksize increases CPU consumption considerably.
[*] Large directories are organized in a similar way as [Fagin's extendible hashing]("http://portal.acm.org/citation.cfm?id=320092&dl=ACM&coll=portal"). Does not use btrees.
[*] Files are embedded directly in directory structure (unless hardlink is created). Thus, ls -la command doesn't have to seek to inodes.
[*] Free space is described in lists of extents rather than bitmaps like in most common filesystem. If a filesystem becomes too fragmented, list of free extents is converted to bitmap.[/LIST]  Current version is 0.9.4. Go to [download]("http://artax.karlin.mff.cuni.cz/%7Emikulas/spadfs/download/") directory. 
 Read [user's manual]("http://artax.karlin.mff.cuni.cz/%7Emikulas/spadfs/download/README") or [description of filesystem internals]("http://artax.karlin.mff.cuni.cz/%7Emikulas/spadfs/download/INTERNALS").


---

### Post by maniacmusician on 2007-02-01
I dont know, never tried it. but from reading the excerpt that you pasted, It sounds decent. One negative thing that I can deduce from it is that it's more prone to fragmentation than a journaling system. But other than that, the author claims that it gets better speed on linux systems

---

### Post by rko618 on 2007-02-02
You say Linus likes SpadFS? Can you post what he said about it?

---

### Post by Polygon on 2007-02-02
ive never heard of it, and it doesnt even have a page on wikipedia, i dont see it supported by commonly used partitioning tools and stuff...is this brand new?

---

### Post by RAV TUX on 2007-02-02
> **rko618 said:**
> You say Linus likes SpadFS? Can you post what he said about it?

> "It doesn't look horrible to me" ~Linus
Thats a high compliment from Linus

---

### Post by RAV TUX on 2007-02-02
> **Polygon said:**
> ive never heard of it, and it doesnt even have a page on wikipedia, i dont see it supported by commonly used partitioning tools and stuff...is this brand new?Yes pretty new I read about in the February issue of Linux Pro Magazine...

article bills it as the "New Non-Journaling Filesystem, SpadFS"
> 
Mikulas Patocka created SpadFS as part of his PhD thesis, and released it to the world, generating a big discussion primarily about Mikula's design.

---

### Post by manmower on 2007-02-02
Linus has [commented on SpadFS](http://lkml.org/lkml/2006/12/29/165) in the kernel mailing list too:
[quote="Linus Torvalds"]I was hoping that something like SpadFS would actually take off, because 
it seemed to do a lot of good design choices (having inodes in-line in the 
directory for when there are no hardlinks is probably a requirement for a 
good filesystem these days. The separate inode table had its uses, but 
indirection in a filesystem really does suck, and stat information is too 
important to be indirect unless it absolutely has to).

But I suspect it needs more than somebody who just wants to get his thesis 
written ;)

		Linus[/quote]

---

