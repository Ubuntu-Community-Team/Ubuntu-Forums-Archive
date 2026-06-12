---
title: "Ubuntu &amp; buffer overflows"
date: 2006-09-13
forum: Server Platforms
---

### Post by perianmellon on 2006-09-13
I'm working on a exploiting a buffer overflow vulnerability for a class and was just curious if the latest release of Ubuntu has implemented any buffer overflow security (non-executable stack, etc).  If it has is there an older version that doesn't?

Thanks!
- K

---

### Post by Klaidas on 2006-09-13
Like, add some buffers specially for owerflowning in a class?
Ummm, NO :-D

---

### Post by perianmellon on 2006-09-13
Sorry, maybe I was unclear, and likely I should have posted in the beginner’s section, because I'm slightly unsure where buffer overflow protection is implemented.

When I said class, I meant it is an assignment for a course I'm taking:
[http://www.ise.gmu.edu/~xjiang/ISA797/schedule.html](http://www.ise.gmu.edu/~xjiang/ISA797/schedule.html) 

I know for example, that fedora core 5 has an non-executable stack, I was just curious if Ubuntu has implemented any manner of protection against buffer overflows.  Or am I completely mislead, and buffer overflow protection is implemented in the kernel?

---

### Post by daxelrod on 2006-09-17
A non-executable stack requires hardware support, and indeed would most likely be in the kernel. Not every architecture the kernel is compiled for supports a non-executable stack. However, x86 does (its mechanism is the [NX bit]("http://en.wikipedia.org/wiki/NX_bit")), and I think* it was enabled by default from kernel version 2.6.8 and on.

Also, keep in mind that a non-executable stack [is not enough to prevent all buffer overflow attacks]("http://en.wikipedia.org/wiki/Return-to-libc").

I am sorry that I am unable to more specifically tell you what support Ubuntu provides for this.

*The reason I said "I think"...
The Wikipedia article linked above claims this in its [Linux section]("http://en.wikipedia.org/wiki/NX_bit#Linux"), unfortunately most of the other sources I found cite the Wikipedia article. The [release notes for version 2.6.8 of the kernel]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.8") say that a patch is available, but do not say whether it's on by default. (Search for the text "NX (No eXecute) support for x86" in the release notes).

---

