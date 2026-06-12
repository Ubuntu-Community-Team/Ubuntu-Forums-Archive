---
title: "Squid Web Cache Proxy Server and automated Page Pre Caching"
date: 2009-07-29
forum: Server Platforms
---

### Post by ant2ne on 2009-07-29
I've set up 2 squid Web Cache Proxies and they are working great! I'm preparing to move the proxie servers into production.

I'm using webmin for configuration as much as possible. And I'm using sarg for report running.

One thing I'd like to be able to do is to tell squid to be certain that it has up to date (checks daily) caches for given web pages. Either automatically once a day the proxy needs to refresh the cache on those pages, and/or refuse those pages to be over written (prioritizing) by other pages being cached. I'm sure that squid can do this, but I'm not sure where to begin. Or even what I'm describing is technically called. And is there a way to configure this all through webmin?

---

