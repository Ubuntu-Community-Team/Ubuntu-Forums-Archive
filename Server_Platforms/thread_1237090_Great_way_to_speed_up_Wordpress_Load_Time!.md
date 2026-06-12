---
title: "Great way to speed up Wordpress Load Time!"
date: 2009-08-11
forum: Server Platforms
---

### Post by JohnLau on 2009-08-11
[I am not sure if I posted this in the wrong place... Please help me to move it to the right place!]
Hi guys,
I just did some experiment on my Wordpress site and found several possible ways to boost Wordpress load time! :lolflag:

**1. Use lighttpd instead of Apache**

Lighttpd is much lighter then Apache (lol) and according to my  little test, it is faster then Apache by about one second!
Follow the [ubuntu wiki]("http://www.google.com.hk/url?sa=t&source=web&ct=res&cd=1&url=https%3A%2F%2Fwiki.ubuntu.com%2FLighttpd%252BPHP&ei=GvOASs--EImi6QOV26jFCQ&usg=AFQjCNFE9O2puaf_Xw2cQUib4l9w7uhy7A&sig2=tYPlEGNHV-DrdAAm8YQRAA") for detailed guide.

**2. Apache + DB-Cache + TMPFS**

I found lighttpd too difficult to configure, then I switched back to Apache and installed the DB-Cache Wordpress Plugin, afterwards, I used tmpfs to store the cache... the result is Super-Fast Wordpress!
Detailed Guide on [my very own site]("http://compustorm.serveblog.net/2009/08/what-i-did-this-time-to-make-my-site-faster/")

Before the tweaks, my wordpress load time is more then 3 seconds, but afterwards it is reducewd to around 1
Second!:guitar:

Hope this helps you all! 

John

---

