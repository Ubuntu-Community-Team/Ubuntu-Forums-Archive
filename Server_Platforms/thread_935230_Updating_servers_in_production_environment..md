---
title: "Updating servers in production environment."
date: 2008-10-01
forum: Server Platforms
---

### Post by gogo242 on 2008-10-01
Just a random question...

I'm running a postfix server in a production environment.  What does anyone suggest as best practices for upgrading the OS?

---

### Post by HermanAB on 2008-10-01
I suggest that you make a Virtual Machine from the physical machine and test everything there before messing with a production server.  If you virtualize the server, then you can save a copy of it on a DVD and roll back whatever screw-ups happened very quickly, by simply starting up the old working copy.

Note that you can stop postfix for up to 4 days, without losing mail, since the senders will retry delivery every few hours before eventually giving up.  Therefore you can do your upgrade over a weekend and be pretty sure that provided you have it running again by Monday, nothing will be lost.

BTW, while you are at it, have a look at Citadel.  It is way better for most purposes and zero maintenance.

Cheers,

Herman

---

