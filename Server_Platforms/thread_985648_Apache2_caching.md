---
title: "Apache2 caching"
date: 2008-11-17
forum: Server Platforms
---

### Post by Vegan on 2008-11-17
Is there an option to adjust the cache in Apache2, my server has lots of RAM and I would like to tweak Apache to use it.

:)

---

### Post by MJN on 2008-11-18
You say 'adjust' but unless you've enabled/configured it to do so Apache doesn't cache anything.
 
If you're using Apache 2.2 (Feisty onwards) then there are now mature (stable) caching capabilities available - see [http://httpd.apache.org/docs/2.2/caching.html](http://httpd.apache.org/docs/2.2/caching.html) for details.
 
Are you sure disk access is your bottleneck?
 
Mathew

---

### Post by Vegan on 2008-11-19
I was hoping to make the old IBM as fast as possible by using the RAM to cache things like logo's and frequently used parts. I noticed PHP has some cache capability so I speculated what benefits can be used with Apache2 generally.

I know the Linux kernel supports caching itself so I wonder if the kernel itself can help speed the server with the additional RAM available?

I have the DEFLATE enabled and that made a huge difference in performance. Pages now display 3x faster. Fast is desirable.

:guitar:

---

### Post by MJN on 2008-11-19
Be very careful with compressing content as many browser cannot handle it. This is particularly true with old and/or customised/obscure browsers on 'non-conventional' access devices such as mobiles, PDAs etc.

Incidentally, if you are successfully using DEFLATE to compress content then one can only assume that your upload bandwidth (or your users' download) is restricted (dialup perhaps?) in which case caching content server-side is probably not going to help you. The requirements for server-side caching and compression are often diametrically opposite.

Mathew

---

### Post by Vegan on 2008-11-20
I have asked some friends who still have dial-up as high-speed is unavailable and they say it works well. Mind you everyone has at least IE5 or better. Firefox 2 or better is ok too.

The DEFLATE is intended to benefit slow users.

My site is so fast, its easy to use and never bores a users waiting for "paint to dry".

I agree that caching and compression are somewhat alien, but I suggest index.html and index.html.gz


:guitar:

---

### Post by MJN on 2008-11-20
> **Vegan said:**
> The DEFLATE is intended to benefit slow users.You should realise that it only benefits slow *connections *as there it a CPU processing overhead at both ends.
 
(perhaps that's what you meant)
 
Mathew

---

### Post by Vegan on 2008-11-20
My server has a Pentium III running at 667 MHz so its probably 20x slower than 99% of my users.

My server is seriously under utilized so why not DEFLATE content for those who have < internet than me. I am lucky to have very fast internet.

---

