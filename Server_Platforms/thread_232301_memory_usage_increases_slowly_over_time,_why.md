---
title: "memory usage increases slowly over time, why??"
date: 2006-08-08
forum: Server Platforms
---

### Post by tlyczko on 2006-08-08
I have VMware Server running on Ubuntu LTS as the host.

Over a period of a few hours, I have observed memory usage rise slowly from 100-something MB to 250-plus MB.

I am observing this in the web-based VMware Management Interface.

Why is this happening, and what can I do about it??

Thank you, Tom

---

### Post by rattlerviper on 2006-08-08
> **tlyczko said:**
> I have VMware Server running on Ubuntu LTS as the host.

Over a period of a few hours, I have observed memory usage rise slowly from 100-something MB to 250-plus MB.

I am observing this in the web-based VMware Management Interface.

Why is this happening, and what can I do about it??

Thank you, Tom

When it creeps up like that it is called Memory leak.  It is a known problem with FireFox, not sure if it is with VMWare.  Also keep in mind that Linux uses all free RAM as disk cache, so that what you are seeing might not be of any concern. If you check System Monitor/Processes  How much memory is it showing that VMWare is using?

---

### Post by ndube on 2008-01-21
I also have been experiencing this problem. What did you end up doing to resolve the issue?

---

### Post by Sidewinder1 on 2008-01-24
Yes, I am experiencing the same thing and was about to post the same question. If it's truly a cache situation is there a way to minimize this. I have a gig of ram and after a few hours I end up with 93 Meg (out of over 1000) left. I have, in fact checked out 'processes' and they all together don't even total 300 Meg. This is quite perplexing; can anyone assist?
Thanx

---

