---
title: "Encryption of privoxy cache"
date: 2009-12-26
forum: Security
---

### Post by viki__ on 2009-12-26
Hi All,

Can anybody tell me if Privoxy or Tor is caching the data anywhere in the filesystem? If so, is there any standard practice to encrypt it?

Thanks

---

### Post by bodhi.zazen on 2009-12-27
privoxy is a non-cacheing proxy =)

See 4.12 on this page :

[http://www.privoxy.org/faq/misc.html](http://www.privoxy.org/faq/misc.html)

This is "fine" as most applications (firefox) will cache by default (well it depends on what you are wanting to use a proxy for exactly =) .

TOR does not chache data on your HD either. 

You will want to configure your browser, however, to clear your cache and other private data. Configuration varies by browser or if you wish you can add extensions and/or the tor button.

---

