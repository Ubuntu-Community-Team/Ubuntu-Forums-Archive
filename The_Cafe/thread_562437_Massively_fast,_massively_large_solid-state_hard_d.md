---
title: "Massively fast, massively large solid-state hard drive unveiled"
date: 2007-09-28
forum: The Cafe
---

### Post by Sporkman on 2007-09-28
[http://hardware.slashdot.org/hardware/07/09/28/176213.shtml](http://hardware.slashdot.org/hardware/07/09/28/176213.shtml)

> 
TG Daily reports that the company Fusion io has presented a massively fast, massively large solid-state flash hard drive on a PCIe card at the Demofall 07 conference in San Diego. Fusion is promising sustained data rates of 800Mb/sec for reading and 600Mb/sec for writing. The company plans to start releasing the cards at 80 GB and will scale to 320 and 640 GB. '[Fusion io's CTO David Flynn] set the benchmark for the worst case scenario by using small 4K blocks and then streaming eight simultaneous 1 GB reads and writes. In that test, the ioDrive clocked in at 100,000 operations per second. "That would have just thrashed a regular hard drive," said Flynn. The company plans on releasing the first cards in December 2007 and will follow up with higher capacity versions later.'

---

### Post by sp0onman on 2007-09-28
i would love to have one, but i dont think i will be prepared to pay the sort of money these things are gonna cost.

---

### Post by Fbot1 on 2007-09-28
It's about time.

---

### Post by Rupertronco on 2007-09-28
I had a solid state disk, it cost me far too much money for the whole month and a half it lasted.

---

### Post by n3tfury on 2007-09-28
> **Rupertronco said:**
> I had a solid state disk, it cost me far too much money for the whole month and a half it lasted.

ok, what brand/model was it so we know what to throw caution at?

---

### Post by BoyOfDestiny on 2007-09-28
> **n3tfury said:**
> ok, what brand/model was it so we know what to throw caution at?

Seriously.

Personally, if I decide to fix my old desktop (which at this point means new cpu + mobo + ram... lol), I'd like to get a 8gig or 16gig solid state drive and just stick / on there with ext2 or what have you. 

To the user whose drive died, what filesystem did you use? Solid State can handle unlimited reads, but has limited rewrites... So something like ext2 would be better... And did you stick swap on it? That would definitely shorten how long it would last...

---

### Post by dustinharriman on 2007-12-09
**I highly recommend that you use reiserfs on any flash media such as a USB flash drive**, **not ext2 nor ext3**.  I learned this the hard way when [I set up a completely solid-state Ubuntu PC]("http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1&p=65") that (consumes a mere 11 Watts of power).

Basically, when it comes to flash media, if you use ext2, you do not get journalling, which reiserfs could provide for you.  And ext3 will shred itself apart after a couple weeks regular use, [see this explanation why]("http://lists.soekris.com/pipermail/soekris-tech/2002-May/000328.html").

This might explain why the previous posters in this thread ran into trouble.

---

