---
title: "apt-cacher-ng and a proxy server"
date: 2009-11-20
forum: Server Platforms
---

### Post by nigelenki on 2009-11-20
I need to use an HTTP proxy to reach the Internet!

How do I configure apt-cacher-ng to use an http proxy?  It seems to not do that...

Simple enough question.

---

### Post by Akita on 2009-11-21
Look at /etc/apt-cacher-ng/acng.conf.

There's a "Proxy" config option.

---

