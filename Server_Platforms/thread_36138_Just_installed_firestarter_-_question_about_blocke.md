---
title: "Just installed firestarter - question about blocked connections"
date: 2005-05-22
forum: Server Platforms
---

### Post by AJCrowley on 2005-05-22
Firestarter's been running on my Hoary laptop for the last 12 hours or so, and has blocked some 68 connection attempts in that time. I know more or less jack sh** about networking and security in general, and so was wondering if the good people here could tell me whether or not any of the attempts represent any sort of severe security breach on my machine.

The biggest offender seems to be 61.172.249.201, which has been periodically attempting to connect to ports 1026 and 1027 via UDP; a bit of googling suggests this is a known source of would-be windows messenger spam, so I assume it doesn't represent a major problem. There are also a number of other sources of multiple attempts to connect to 1026 and 1027 using UDP. Is this normal and harmless (or at least, no more than a nuisance), or should I be worried?

More worryingly, at least to this n00b, I've had two attempts to connect via TCP to specific services, one to ldap through port 389, and another to VNC through port 5900. To my knowledge, I'm not running either of these services, but it'd be nice to know whether I should be taking any more aggressive security measures.


Thanks in advance for any/all helpful answers that may be forthcoming, and apologies for the rather tragic extent of my ignorance.

---

### Post by N'Jal on 2005-05-22
I have used firestarter and it blocked several thousand attacks a day. Now this either means that i make a rather large appearence on the net for hackers, or firestarter is very thourugh and picks up everything.

As for the whole windows messenger thing, you should be ok, due to the fact that you don't have windows messenger.

But then again, someone with more experience than me should confirm

---

