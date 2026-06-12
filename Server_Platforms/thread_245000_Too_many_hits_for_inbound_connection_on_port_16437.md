---
title: "Too many hits for inbound connection on port 16437 (TCP&amp;UDP)"
date: 2006-08-27
forum: Server Platforms
---

### Post by d3ck4 on 2006-08-27
Firestarter detecting hits for inbound connection on port 16437 (TCP&UDP) in every single second. Is this related to any issue according to the latest internet worm or something :confused:? My connection is getting slower than usual :(. Is there anyone here got the same problem?

---

### Post by skymt on 2006-08-28
A quick Google for "port 16437" came up with [this](http://www.brgprecision.com/openpl.html). Looks like it's used by NTP (network time protocol). I also get a lot of hits on this port. It's nothing to worry about for most users. It may be a new worm attacking a hole in ntpd. Just live behind a router.

---

