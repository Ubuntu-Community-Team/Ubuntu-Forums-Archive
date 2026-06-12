---
title: "News from FFADO regarding recent FireWire conflict."
date: 2010-01-05
forum: Ubuntu Studio
---

### Post by Th3Professor on 2010-01-05
Here is a recent message from over on ffado.org:

> 

**Rumors about FFADO and the new firewire stack**

                                                 Submitted by arnonym on Mon, 12/28/2009 - 23:17.

      The last weeks have seen a few rumors and lots of questions: Is ffado running with the new firewire stack?

 The short answer as of this writing: No

 Read on for the longer answer...
 
Running FFADO 2.0 or later on the new stack requires kernel 2.6.32 or later. And a yet unreleased version of libraw1394 (>2.0.4). Making ffado run on the new stack revealed some bugs and not-yet-implemented things in the new stack and the libraw1394 compatibility code because audio streaming is using the firewire stack in more demanding and advanced ways then for example hard-disk access.

But the good news is that this is actually worked on and working on the developers machines. Once all the necessary dependencies are released, its up to the distributions to ship the new versions (and finally completely disable the old stack).

And there are also forces at work to implement the streaming in kernel-space. Of course this will be on the new stack only...

Updates will of course be posted here.



Source:

[http://ffado.org/?q=node/1316](http://ffado.org/?q=node/1316)

---

### Post by bluesscream on 2010-01-05
Here ffado 2.0~rc2+svn1569 in karmic amd64 with jackd 1.9.4 from frasten's ppa (tx Andrea P.) is working stable on all ubuntu's 2.6.31 and 32 kernels. libraw 1394-8 v.1.3.0 (old stack?) is installed as well as libraw1394-11 v.2.0.4 (new stack?). libraw1394 v.2.0.5 is available [here]("http://sourceforge.net/projects/libraw1394/") if one is dying to test ffado's bleeding edge - might be better in lucid alpha. I don't see the problem, in my Ubuntu karmic 9.10 untouched kernels old stack is not disabled.

---

### Post by AutoStatic on 2010-01-06
The new stack is called **firewire-ohci** and it's blacklisted in */etc/modprobe.d/blacklist-firewire.conf* in Karmic. You have to use either the old stack or the new one, you can't use them both at the same time. So one has to be disabled, in Karmic it's the new stack so the default stack is the old one. So no need to worry.

---

### Post by bluesscream on 2010-01-07
> **AutoStatic said:**
> The new stack is called **firewire-ohci** and it's blacklisted in */etc/modprbe.d/blacklist-firewire.conf* in Karmic. You have to use either the old stack or the new one, you can't use them both at the same time. So one has to be disabled, in Karmic it's the new stack so the default stack is the old one. So no need to worry.

Tx, I'm on my way to lucid now, here ohci is blacklisted  too, so  I still  can use kernel 2.6.31-9-rt without any modifications.

---

