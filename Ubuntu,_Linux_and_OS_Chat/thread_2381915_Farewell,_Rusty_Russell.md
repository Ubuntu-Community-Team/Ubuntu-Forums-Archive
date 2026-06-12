---
title: "Farewell, Rusty Russell"
date: 2018-01-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Mobile Data Solutions on 2018-01-06
Stumbled upon this morning. I had no idea Rusty had resigned as a kernel contributor, and had not seen this from last August.

If you don't know who Rusty Russell is, well, skip this post!

[https://patchwork.kernel.org/patch/9900173/](https://patchwork.kernel.org/patch/9900173/)

I know his contributions are a bit a controversial, depending on one's perspective. No matter what you think of him; there's no question he's had a huge impact on Netfilter and the Linux kernel's handling of network packets since 1999-2000 or so. Long time. He deserves a big THANK YOU for all the work he's done on iptables, and for his DOCUMENTATION - a concept still sorely lacking in the open source community and larger dev community in general. 

Maybe he decided to bail in case nftables ever gets traction! Lol. 

Excepted below:

```
Patchwork MAINTAINERS: Remove from module & paravirt maintenancelogin 
register 
mail settings
Project: LKML : patches : project info : other projects about
Submitter	Rusty Russell
Date	Aug. 14, 2017, 9:31 p.m.
Message ID	<877ey5q1k3.fsf@rustcorp.com.au>
Download	mbox | patch
Permalink	/patch/9900173/
State	New
Headers	show
Comments
Rusty Russell - Aug. 14, 2017, 9:31 p.m.
It's been 20 years since I became a kernel maintainer, so despite how
much I'm loving my new career, this patch elicits deep feelings[0].

I went to 1997 USENIX, my first conference.  I remember[1] standing
around with Alan Cox, Linus, Ted Ts'o and David Miller as they wrote
the code for the BKL on a napkin.  I listened in awe as this
homeless-looking guy described porting Linux to the Ultrasparc, and
then described how he then proceeded to beat Solaris on *every single*
lmbench microbenchmark.[2]

A lot of it I didn't understand, but I got home knowing that I had to
work with this random bunch of hackers.  I had some firewalling hacks
which I turned into ipchains, and sent it to DaveM with a config
option to switch between the old ipfwadm code and my new code.  He
liked it so much he replaced ipfwadm entirely, and I woke up one day
as kernel firewall maintainer[3].

I found someone to fund my work the next year, and suddenly I was
doing my dream job full time.  I flew myself around Australia visiting
every LUG to convince them to come to the first Australian Linux
conference.  And of course, DaveM was top of my list for speakers.

There was so much work to do on the kernel; everywhere you'd look
there was code which could be simplified, improved.  I read the module
code and was so horrified at its complexity that I rewrote it, not
realizing how epic that would be.  Of course I broke lots of things;
halfway through the patch series I broke SCSI, so Linus applied up to
that point and we had half a module subsystem for a while; I was
literally in the airport in Tokyo on my way to Spain when he applied
it, too.  Every arch maintainer woke up to find they had to implement
a whack of complex relocation code, and I got a lot of grumbling.[5]

But one person disagreed with my approach so much and so continuously
that I developed a dread of reading my mail every morning: eventually
I wrote a filter to send their mail to a separate mbox, which I've
still never read and don't intend to.

But mainly, it was a huge amount of fun.  I got to hack, and geek out
with hackers all around the world.  When I flew into San Jose for the
first time, DaveM offered to pick me up: turns out he had a two seater
so I rode squashed under the rear glass on the overside parcel shelf
to see the sights (Sun campus, Berkeley).  Back home, I moved to
Canberra to join the legendary group of hackers at OzLabs.

The mailing list changed: I gradually learned not to be an *******
(unless, y'know, it was *really* funny, and eventually not even then).
Most of my peers trended the same way.  The kernel itself became more
formal, more complex, and giant overarching changes became far, far
fewer.  There are still horrible APIs (the return value of
copy_to/from_user, using the same type for list heads and elements, to
name two[7]), but the modern calculus of disruptive changes means
sometimes we simply step over the broken paving stones instead of
repairing them.

I built a team around netfilter, then handed maintenence off to Harald
Welte and ceased contributing: I wanted him to own it entirely.  I was
more nervous handing module maintenance over to someone I've never
even met or spoken to, but it's clear now that with Jessica Yu I have
scored 2 for 2.  I'm as proud of choosing them as of any individual
piece of kernel code[8].

To my fellow maintainers: stay harsh on code and don't be afraid to
say "No" or "Why?"; there really are more bad ideas than good ones,
and complexity is such a bright candle for us hacker-moths.  But be
gentle, kind and forgiving of your peers: respect from people you
respect is really the only reward that sticks[9].

Farewell all, and I look forward to crossing your paths again!
Rusty.

[0] Which means I'm now going maudle for NINE paragraphs! And no TLDR, bwahaha!
[1] OK, I remember this.  Reality may differ.
[2] There's no recording of this talk, but it was the best technical
    talk anyone has ever given on anything[1].
[3] On the internet, nobody knows you barely passed Computer Networking![4]
[4] OTOH I topped COBOL/Database programming, so I have no idea what happened.
[5] Except DaveM.  I'd written test reloc code for sparc/spac64, but
    he didn't know that so he just cheerfully reimplemented it.[6]
[6] Those reading this post closely may suspect that I have a massive
    hackercrush on David S. Miller.  Those reading the code closely, of course,
    already feel that way themselves.
[7] But set_bit finally takes a long!  Seriously...
[8] Though the ARRAY_SIZE macro and the poetry in lguest are a close second.
[9] Actually, bitcoin is a nice reward too; it's like crystalized machine
    sweat!

Signed-off-by: Rusty Russell <rusty@rustcorp.com.au>
---
 MAINTAINERS | 2 --
 1 file changed, 2 deletions(-)
Patch
diff --git a/MAINTAINERS b/MAINTAINERS
index 6f7721d1634c..df2ae7621226 100644
--- a/MAINTAINERS
+++ b/MAINTAINERS
@@ -8841,7 +8841,6 @@  F:	drivers/media/dvb-frontends/mn88473*
 
 MODULE SUPPORT
 M:	Jessica Yu <jeyu@kernel.org>
-M:	Rusty Russell <rusty@rustcorp.com.au>
 T:	git git://git.kernel.org/pub/scm/linux/kernel/git/jeyu/linux.git modules-next
 S:	Maintained
 F:	include/linux/module.h
@@ -9949,7 +9948,6 @@  PARAVIRT_OPS INTERFACE
 M:	Jeremy Fitzhardinge <jeremy@goop.org>
 M:	Chris Wright <chrisw@sous-sol.org>
 M:	Alok Kataria <akataria@vmware.com>
-M:	Rusty Russell <rusty@rustcorp.com.au>
 L:	virtualization@lists.linux-foundation.org
 S:	Supported
 F:	Documentation/virtual/paravirt_ops.txt

patchwork patch tracking system
```

---

