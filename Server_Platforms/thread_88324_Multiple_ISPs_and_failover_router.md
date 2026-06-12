---
title: "Multiple ISPs and failover router?"
date: 2005-11-10
forum: Server Platforms
---

### Post by thepoch on 2005-11-10
Hi guys,

I was wondering if iptables in Breezy has support for CONNMARK, specifically, as mentioned here: [http://www.shorewall.net/Shorewall_and_Routing.html](http://www.shorewall.net/Shorewall_and_Routing.html)

I have 2 DSL connections that I need to use. I plan on at least implementing the shorewall method first. But long term would be an automatic failover solution. Anyone have scripts that can possibly be integrated with shorewall that can monitor connections and automatically switch to the working connection when the other is down, then go back up when everything is working fine? I'm looking at [http://www.epr.ch/brb/linux/backroute.html](http://www.epr.ch/brb/linux/backroute.html) for this, but would love to hear suggestions and experiences on both topics.

Thanks!

dex

---

