---
title: "New virtual hyperv ubuntu 18.04 server installed but wget command not working?"
date: 2019-04-18
forum: Server Platforms
---

### Post by justuselinux on 2019-04-18
I'm trying to use the wget command to download squid server from this link [http://www.squid-cache.org/Versions/v3/3.5/squid-3.5.27.tar.gz](http://www.squid-cache.org/Versions/v3/3.5/squid-3.5.27.tar.gz).
However Im getting this "HTTP request sent, awaiting response... 404 Not Found" every time.

I've added this rule to my Sophos Firewall to allow all traffic to and from the server but still with no luck.

 [ATTACH=CONFIG]283047[/ATTACH]

This is probably really simple, any ideas?

Many thanks!

---

### Post by TheFu on 2019-04-18
Use a web browser?  Try lynx, curl, whatever.
But if your server networking isn't working correctly, none of this will matter.  

Also, whenever there are files with versions, those filenames change from week to week, so get the correct name for this week.

---

