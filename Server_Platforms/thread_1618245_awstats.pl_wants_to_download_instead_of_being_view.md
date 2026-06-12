---
title: "awstats.pl wants to download instead of being viewable in browser"
date: 2010-11-10
forum: Server Platforms
---

### Post by MechaMechanism on 2010-11-10
Every time I go to domain.tld/awstats/awstats.pl, it wants to download the pl file.

Do I not have cgi enabled?  The attachments are my apache default config and the awstats config.

---

### Post by dapperdanny77 on 2010-11-10
check 

[http://awstats.sourceforge.net/docs/awstats_setup.html]("http://awstats.sourceforge.net/docs/awstats_setup.html")

have a look at B)

your apache config should include this

---

### Post by MechaMechanism on 2010-11-10
Turns out I did not have cgi enabled.  I had removed it before and forgot to re-enable it.  D'oh!

---

