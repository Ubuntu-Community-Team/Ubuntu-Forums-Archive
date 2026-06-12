---
title: "named error on server log"
date: 2012-05-18
forum: Security
---

### Post by phillw on 2012-05-18
Hi,

Whilst I do keep an eye on the /var/log/message file, this one has got me well beat!

```
 named[1216]: error (unexpected RCODE REFUSED) resolving '180.193.78.38.in-addr.arpa/PTR/IN': 38.109.170.13#53

```

One IP address reckons to be from the [ Philipines ](http://www.utrace.de/ip-adresse/180.193.78.38), the other from [ Washington USA ](http://www.whoismind.com/ip/38.109.170.13.html)

I know named is the dns daemon, but more than that I'd be grateful of an explanation of.

Thanks,

Phill.

---

### Post by papibe on 2012-05-18
Hi phillw.

It looks like an spammer is trying to hit your server with phony domains.

Regrads.

Source: [this]("http://www.linuxquestions.org/questions/linux-server-73/unexpected-rcode-refused-and-servfail-915631/").

---

