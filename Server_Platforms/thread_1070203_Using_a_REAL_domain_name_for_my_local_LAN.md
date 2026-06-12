---
title: "Using a REAL domain name for my local LAN?"
date: 2009-02-14
forum: Server Platforms
---

### Post by samosamo on 2009-02-14
Does anyone have a sample dnsmasq.conf where they used a real domain name for their LAN?  When I say "real domain" I mean one that is used on the internet.

I'm having trouble configuring the local LAN with a real domain name.  The local DNS server always requests the upstream servers for info, even though it has a successful match already.  I can't find the option to stop it from doing this.

What I did temporarily was set the "local=/mydomain.com" option but that means you can't go to an internet-side site like "www.mydomain.com" which is not defined in the local DNS, because it does not need to be.

---

