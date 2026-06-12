---
title: "Unable to install libt1-dev on Ubuntu 15.04 Kilo"
date: 2015-08-11
forum: Server Platforms
---

### Post by mikeossur on 2015-08-11
Hi Everyone.  I just installed Ubuntu server 15.04 Kilo.  I am compiling PHP 5.3.29.   I need t1lib or as it's install name libt1-dev.  For some reason this lib does not exist.  Can anyone give me a reason why it's not available and how to get around this problem?

Thanks,
Mike

---

### Post by PaulW2U on 2015-08-11
*Post moved to its own thread in **Server Platforms**.*

---

### Post by mikeossur on 2015-08-11
I suspect either the name has changed, it is part of another package or a over site.

---

### Post by mc4man on 2015-08-11
t1lib was only provided thru 14.04
15.04 is a short-term release, (EOL in 6 months)  & PHP 5.3.29 was EOL some time ago, sounds like a good pairing?

---

### Post by mikeossur on 2015-08-11
I was with debian. We are upgrading to newer hardware. I thought I would give Ubuntu a spin. Silly me, thinking installing software onto a server should be consistent.   Ok...I can manually install.  Thanks,

---

### Post by mikeossur on 2015-08-11
Never mind. I just removed --with-t1lib   It was probably not required anyway. This is what happens when you have years of legacy stuff. Most of which is no longer needed.  Thanks for your help on this. This stuff can be frustrating at times as you may already know, Lol

---

