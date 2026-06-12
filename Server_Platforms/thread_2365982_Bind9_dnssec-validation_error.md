---
title: "Bind9 dnssec-validation error"
date: 2017-07-12
forum: Server Platforms
---

### Post by stlu on 2017-07-12
Hello,

I have a Ubuntu server running Bind9.  It use it to give the computers on my LAN some local addresses.  Then I configured it to use my Internet modem/router as a forwarder.

All seemed fine for a bit.  I could resolve site URLs without issue.  Then I tried to go to [www.mozilla.org]("http://www.mozilla.org"), and my browser returned an error.  I found that my instance of Bind9 was able to resolve "mozilla.org" but not "www.mozilla.org".  From another location, I used the dig command on both those URLs, and the only difference was that "www.mozilla.org" was a CNAME while "mozilla.org" was an A record.

I tried various solutions that I found online, and the one that worked was changing **dnssec-validation auto **to **no.**

My question is, why was this necessary in order to resolve a CNAME?  Is there a better solution than to turn off this feature completely?

---

