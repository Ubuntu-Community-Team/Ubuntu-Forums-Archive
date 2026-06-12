---
title: "squid exclude URL from caching"
date: 2010-02-17
forum: Server Platforms
---

### Post by liverpoolatnight on 2010-02-17
Hi all :) 

How do i exclude some URL from the proxy caching at squid.conf as i dont wont to cache youtube, mediacafe etc, I know i can block site by create a file like bad-sites.acl, then adding it to squid.conf but that blocks it.

Thanks :popcorn:

---

### Post by mbehamin on 2010-02-18
just in your squid.conf file add following options 

[I]acl NoCacheACL urlpath_regex $yourdomainname
no_cache deny NoCacheACL[/I]

---

### Post by liverpoolatnight on 2010-02-20
> **mbehamin said:**
> just in your squid.conf file add following options 

[I]acl NoCacheACL urlpath_regex $yourdomainname
no_cache deny NoCacheACL[/I]
My logs
1266669973.591   5509 192.168.1.92 TCP_MISS/200 1809018 GET [http://v22.lscache1.c.youtube.com/videoplayback?](http://v22.lscache1.c.youtube.com/videoplayback?) - DIRECT/ video/x-flv

Cheers :)

---

