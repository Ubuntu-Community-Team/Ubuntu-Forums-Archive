---
title: "DDclient multiple IPs"
date: 2010-02-17
forum: Server Platforms
---

### Post by Azure1203 on 2010-02-17
Alright, I'm trying to update multiple dynamic IPs on OpenDNS through ddclient.

Is it even possible?

I get as far as where I should actually get the IP address from, and I'm stuck.  Obviously I can't use something like 'myip.dnsomatic.com' as it would give me my own address.

Any help?

---

### Post by noway2 on 2010-02-17
I had to re-read your post a couple of times and admit that I am confused.

ddclient is supposed to update the dns forwarder of your current IP address when it changes.  If you have multiple IPs, each one that updates would need to register the update.  

I guess I don't really understand what you are trying to do or what problem your running into.

---

### Post by Azure1203 on 2010-02-17
What I'm actually trying to do, and it isn't working is use DNSOMATIC to keep track of an IP Address on a router running DDWRT, and send an update to OpenDNS if it changes.

3 different routers, each with a different external address.

Well it isn't working, so I'm looking at other ways of doing the same thing.

I was wondering if ddclient can be configured to do something similar.

---

