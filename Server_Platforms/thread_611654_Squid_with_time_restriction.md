---
title: "Squid with time restriction"
date: 2007-11-13
forum: Server Platforms
---

### Post by ariek on 2007-11-13
Hi,

Is it possible to configure Squid proxy, probably combined with a plug in, to allow maximum session time/duration? I.e. I would like to prevent kids to surf longer than 2 hours per (any time of the) day.
Hopefully my question is clear enough.

Arie

---

### Post by pete.dawgg on 2007-11-13
squid does not have plug-ins, but it supports an extremly wide and flexible range of acls. all is said here: [http://wiki.squid-cache.org/SquidFaq/SquidAcl](http://wiki.squid-cache.org/SquidFaq/SquidAcl)

a countdown-timer for a fixed amount of webtime might be hard to implement, though; you should probably use sth else

---

