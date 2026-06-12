---
title: "How to telnet to Varnish proxy"
date: 2011-06-06
forum: Server Platforms
---

### Post by R.Bucky on 2011-06-06
I am puzzled on how to login to Varnish proxy using telnet. Using Terminal, I "telnet localhost 6082". The prompt returns with "authentication required." I am uncertain what to do next. I have read [http://www.varnish-cache.org/trac/wiki/CLI]("http://www.varnish-cache.org/trac/wiki/CLI"), however I am at a loss.

Any help would be appreciated.

---

### Post by wica on 2011-09-21
varnish require a auth challenge, unless you do this manuel (checklib/libvarnish/cli_auth.c ) ..... it is not possible.

It is beter to use varnishadm, this does it for you.

---

