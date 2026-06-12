---
title: "Bind9 on Internal Domain"
date: 2008-07-06
forum: Server Platforms
---

### Post by Nfzgrld on 2008-07-06
For years I have been running an internal domain. That is to say, it has a nonstandard extension (.hom) that exists only in my local network. While running WindowsNT and 2K all those years it was very simple. I set up the records in DNS and had DHCP include it as the third DNS server. Everything worked fine.

Now I'm running Ubuntu 8.04 server and after setting up the same configuration, basically, I can't resolve any of the internal domains from any of the internal clients. Can't even ping them. Even after cutting the DNS servers list in DHCP to 2 and making the internal one first on the list it still doesn't work. I've working on this for some time now. Any idea what I'm missing?

---

### Post by azadpanchi on 2008-07-25
The issue needs to be investigated further, I recommend using 'dig' to find out where this maybe failing.  The trace option is especially good for this, dig gentoo.de +trace.

[http://www.madboa.com/geek/dig/](http://www.madboa.com/geek/dig/)

---

