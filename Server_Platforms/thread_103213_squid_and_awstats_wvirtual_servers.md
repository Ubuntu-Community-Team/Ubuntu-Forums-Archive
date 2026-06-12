---
title: "squid and awstats w/virtual servers"
date: 2005-12-13
forum: Server Platforms
---

### Post by nomediakings on 2005-12-13
I set up squid as a httpd accelerator for my server and it was working well, but I found that it was logging all data to a single access.log and thus screwing up the stats programs I'd set up for virtual servers. Is there a way for squid's access.log data to include the virtual server name, so I can point awstats at it to extract the pertinent data for virtual hosts? Or a way to train squid to put access data in different virtual host logs, as apache2 does?

I find these forums hugely useful, so much so that I've never had to post until today -- I could search them for most of my answers. This, however, has stumped me.

Jim

---

