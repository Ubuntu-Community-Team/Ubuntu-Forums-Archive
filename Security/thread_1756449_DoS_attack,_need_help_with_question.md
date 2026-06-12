---
title: "DoS attack, need help with question"
date: 2011-05-12
forum: Security
---

### Post by guessswh0 on 2011-05-12
Hi there,

This is probably more of a php or apache question, but I am hoping you guys could help (the box is running Ubuntu...).  I have a guy who does a DoS attack on a website that is being run.  I can't install applications on this since it is not my box.  Is there a apache.ini or php.ini setting that I can set to limit the number of http requests per IP?

Basically, the guy just floods the server with HTTP requests, bringing down the site.  The hosting company aparrently has nothing on their network to detect and prevent this.

Any config option to help would be awesome.

Thanks

---

### Post by Lars Noodén on 2011-05-12
iptables can [limit the number of connections](http://netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-7.html) per minute/second/hour, or just block that host completely.

Here is a [tutorial on limiting](http://www.debian-administration.org/articles/187) just substitute the SSH port for your webserver's port, probably port 80.

---

