---
title: "Milter problem - can't start dkim-filter"
date: 2008-05-21
forum: Server Platforms
---

### Post by Mark F on 2008-05-21
Hi - I'm setting up an 8.04 server mail filter using the [server guide instructions]("https://help.ubuntu.com/8.04/serverguide/C/mail-filtering.html"). 

The story so far: postfix/dovecot/roundcube worked fine. I installed all of the recommended software. I noticed an installation error for dkim-filter:

```
Setting up dkim-filter (2.5.4.dfsg-0ubuntu2) ...
Starting DKIM Filter: dkim-filter: /etc/dkim-filter.conf: at least one selector and key required for signing mode
invoke-rc.d: initscript dkim-filter, action "start" failed.
dpkg: error processing dkim-filter (--configure):
 subprocess post-installation script returned error exit status 78
Errors were encountered while processing:
 dkim-filter
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I ignored the error :redface: and made all of the other alterations recommended on the server guide. Now I can't send or receive mail.:confused:

I'm now thoroughly confused and don't understand what is going on! Suggestions gratefully received!

---

