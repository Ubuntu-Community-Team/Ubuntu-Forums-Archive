---
title: "Support for hardware-based web server encryption"
date: 2009-10-10
forum: Security
---

### Post by brianmc on 2009-10-10
I'm doing some research into the impact of running a website exclusively over https instead of unencrypted http. I am not having much luck getting easily-understood answers to make credible estimates on the cost of this, and how that scales with a more complex setup than a single web server.

The first, and simplest question, is:

1. If you compare a single web server running https with one running http on the same hardware, what are the the impacts on performance? (For example, for every 100 users/requests the http server supports, the https server will only support 85).

2. Is there crypto hardware supported by Linux that would make question 1 a non-issue?

3. If a site is scaled and distributed using squid caches, what are the repercussions of processing requests exclusively via https? Does this change if the site usage includes a significant number of user-supplied content updates?

Any help with this would be very, very useful.

Thanks!

---

### Post by duanedesign on 2009-11-02
Here is a nice link discussing the differences between http and https when it comes to speed. Also gives some tips for doing your own benchmarking so you can decide for yourself if the trade off is worth it.

[How Much of a Performance Hit http vs. https]("http://serverfault.com/questions/43692/how-much-of-a-performance-hit-for-https-vs-http-for-apache")

---

