---
title: "controlling a socks proxy"
date: 2011-02-27
forum: Server Platforms
---

### Post by roobinatube on 2011-02-27
Hi all, I wonder if you can help me.

I have my desktop set up as a SOCKS proxy, and not only me uses it, some friends do too.

What I would like to know is how to check every now and again what they are using it for... for example the agreement we have is that they only use it to watch BBC iplayer and 4OD etc while they are abroad. What I dont want is them to pointlessly use it for other browsing.

I trust my friends wont, but is there also a way of checking they arent using my connection to download illegal torrents?

I guess best case scenrio would be to be able to whitelist only a few sites per user request. Is this possible?

Thanks for any help!
Roo

---

### Post by HermanAB on 2011-02-27
Use tcpdump to look at the DNS requests on port 53.

---

