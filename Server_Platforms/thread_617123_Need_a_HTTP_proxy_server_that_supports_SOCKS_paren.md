---
title: "Need a HTTP proxy server that supports SOCKS parent"
date: 2007-11-19
forum: Server Platforms
---

### Post by electronixtar on 2007-11-19
Hi all,

I am running Privoxy as a HTTP proxy server with a SOCKS parent 127.0.0.1:13500. But privoxy do NOT support some rare HTTP request verb headers like PUT, PROPFIND, etc. So I have problems running some programs behind firewall like svn, rsync, lastfm.

Squid supports most of HTTP verbs, but Squid is more like a cache and it does not support SOCKS parent.

I also tried Popilo, it does not support exotic HTTP headers either.

So my question is, is there any proxy server that supports:
1. MOST http headers
2. a socks parent
3. user authentication, or IP ACL

---

