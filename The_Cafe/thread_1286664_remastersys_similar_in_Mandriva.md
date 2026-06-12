---
title: "remastersys similar in Mandriva?"
date: 2009-10-09
forum: The Cafe
---

### Post by longtom on 2009-10-09
Hi,

I know this is an Ubuntu forum but I don't want to join another forum just for one question.  So here it goes:

Friend of mine has a network setup in Mandriva installed somewhere.  Knowing that I also dabble a bit in Linux, he asked me what to do to save all his settings and have them readily available in case of fire.

So I told him about remastersys - only to realise later that remastersys is only for Debian based OS.

Is there anything in the Mandriva realm he could do something similar with?

Any suggestions welcome.

---

### Post by Xbehave on 2009-10-09
any backup tool should do it but otherwise
making an archives with 
```

sudo "tar -zPvp --exclude-caches  -c /etc/ > etc.tar.gz"
tar -zPvp --exclude-caches -c ~/.* > home.tar.gz

```
its a bit dumb and included cached info, but it should keep all configs (--exclude-caches doesn't seam to do much and while you could do some regex to exclude any dir with cache in the name its probably not worth it)
you will also need to backup a list of installed programs, i don't know how you would do that under mandriva.

---

### Post by BrokenKingpin on 2009-10-09
I would just use Clonezilla to image his current drive. 

There was a tool for PCLinuxOS that was very similar to Remastersys, which might also work in Mandriva as they are both RPM based. I can't remember the name of the tool though.

---

