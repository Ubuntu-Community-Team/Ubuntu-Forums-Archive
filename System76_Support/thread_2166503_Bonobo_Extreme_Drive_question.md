---
title: "Bonobo Extreme Drive question"
date: 2013-08-09
forum: System76 Support
---

### Post by hawkmage on 2013-08-09
With both  2 regular SATA drives and 2 mSATA drives how do they show up as devices?  Are the mSATA drives addressable as regular /dev/sd* devices or are they treated differently?

---

### Post by phxpx on 2013-08-14
Since nobody answered that for a long time I would like to answer. 
Actually your answer is here : [http://www.debian.org/releases/stable/i386/apcs04.html.en](http://www.debian.org/releases/stable/i386/apcs04.html.en)

But for a short answer your SATA drives are SCSI devices so they should be named sda*,sdb*,sdc*,sdd*.
My msata drive is named as /dev/sda

---

### Post by hawkmage on 2013-08-15
Thanks, that is what I was assuming.

---

