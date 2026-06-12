---
title: "apache2 ssl fail after upgrading to karmic"
date: 2009-11-29
forum: Server Platforms
---

### Post by artheus on 2009-11-29
Hi there!

I've been having a lot of trouble with configuring my SSL, until I found a great tutorial and everything started to work great!

BUT! When I, today, upgraded my dist to 9.10 Karmic Koala, the whole SSL configuration of apache2 failed totally.. Now I can't even start apache2 deamon. And I get the error

*/var/log/apache2/error.log*
```
[Sun Nov 29 17:34:10 2009] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile]
```

So I started searching around some forums (including this) about this problem, and tried the "solution" in those pages, which where eg. moving all the ssl config from sites-available/* to httpd.conf. But no change at all..

What is the difference between the Apache2 in Karmic and the Apache2 in Jaunty? And why am I getting this error?

Thankfully,
Artheus

---

