---
title: "[solved] Unable to access hyperbola.info sites, is it just me?"
date: 2019-08-13
forum: The Cafe
---

### Post by &amp;KyT$0P# on 2019-08-13
Is anyone else having trouble accessing hyperbola.info sites, e.g. [Icedove-UXP wiki page](https://wiki.hyperbola.info/doku.php?id=en:project:icedove-uxp)?

I seem to be getting a persistent DNS error.  Both my web browser and dig wait for several seconds, and eventually DNS lookup fails -
```
$ dig wiki.hyperbola.info

; <<>> DiG 9.11.3-1ubuntu1.8-Ubuntu <<>> wiki.hyperbola.info
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 34971
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;wiki.hyperbola.info.           IN      A

;; Query time: 4037 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: xxxxxxxxxxxxxxx
;; MSG SIZE  rcvd: 48


```

But [https://isitup.org/wiki.hyperbola.info](https://isitup.org/wiki.hyperbola.info) appears to have no problem here and claims the site is up.

So I tried making dig use Google Public DNS server.  But that just result in the same error again.

I'm getting this same error for all hyperbola.info domains that I've tried.  I'm not experiencing this problem with any other sites.  Any idea why I can't connect to hyperbola.info domains?

---

### Post by irv on 2019-08-15
I tried it and it worked for me.
[ATTACH=CONFIG]283811[/ATTACH]

---

### Post by &amp;KyT$0P# on 2019-08-19
Thanks irv.  In light of your response I went to their irc channel.

The answer is that they are doing maintenance on the site, and many DNS servers have not yet picked up the DNS-related changes.  The person I talked to suggested I try using the DNS server 208.67.222.222, which got www.hyperbola.info working (others still don't work, but now I get NXDOMAIN instead of the failure above).  I gather this will also get the other hyperbola.info sites back working for me when the maintenance is done.

---

