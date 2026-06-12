---
title: "how does ext3 work?"
date: 2007-05-23
forum: The Cafe
---

### Post by atlfalcons866 on 2007-05-23
how does ext3 work? does it have a file allcoation table?

---

### Post by Rhox on 2007-05-23
> **atlfalcons866 said:**
> how does ext3 work? does it have a file allcoation table?

Ext3 is basically Ext2 with journaling. Ext2 puts files in single blocks rather than putting them in multiple blocks. So it does not use a file allcoation table.

---

### Post by bonzodog on 2007-05-23
I don't quite understand the reference of your question, so I am going to point you at a wikipedia article:
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

Linux and Unix file systems do not use File Allocation tables. They use a system of inodes to store files, and the ext3 system is also journalled, so it keeps a log of the last 250 or so transactions to the HDD.

---

### Post by starcraft.man on 2007-05-23
Wikipedia to the RESCUE!!!

*superhero music cues in the great and mighty link* [TADA!!!]("http://en.wikipedia.org/wiki/Ext3") *and promptly flies off agian*

edit: rats... bonzo ruined my entrance... *grumbles*

---

### Post by Rhox on 2007-05-23
> **starcraft.man said:**
> Wikipedia to the RESCUE!!!

*superhero music cues in the great and mighty link* [TADA!!!]("http://en.wikipedia.org/wiki/Ext3") *and promptly flies off agian*

edit: rats... bonzo ruined my entrance... *grumbles*

I think he wanted a simplification.

---

