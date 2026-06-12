---
title: "sparc esp scsi driver rewritten in 2.6.22"
date: 2007-04-28
forum: Sun Sparc Users
---

### Post by erm67 on 2007-04-28
It was time, searching this forum it looks like  many has problems with this scsi driver.

[http://vger.kernel.org/~davem/cgi-bin/blog.cgi](http://vger.kernel.org/~davem/cgi-bin/blog.cgi)

> I rewrote the ESP driver because the old one was a rotting pile of poo. I can say that because I wrote the old driver :-) The new one supports so much more stuff, is so much more stable and well architected, and is about half the size of the old one. It's always like that. Furthermore it allows ports to non-sparc platforms. Using this the ncr53c9x.c driver can be deleted (it's a very old clone of my original ESP driver chopped up to be portable to other platforms) and a lot of scsi mid-layer cruft kept around specifically for these drivers can die.

---

