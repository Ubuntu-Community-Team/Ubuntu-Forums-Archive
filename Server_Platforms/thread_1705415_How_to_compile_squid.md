---
title: "How to compile squid ?"
date: 2011-03-12
forum: Server Platforms
---

### Post by honey_bee on 2011-03-12
hi,
    I have installed ubuntu in my system .Squid is by default in it. I want to compile delay_pools feature in squid. 

Normally we download source code file in tar.gz format ,uncompressed it  and then install it. If we want to compile any thing  we can also do it.

Here in my case there is already squid installed during installation  process.  Kindly guide  that how can I compile my current  installed squid is there any source code of squid in it  ? 
thanks in advance.
honey

---

### Post by koenn on 2011-03-12
```
apt-get source squid
``` should give you the source of the squid you have installed. (you need the deb-src repos enabled in your sources.list

this apt howto tells you more/ It says "obsolete" but looks like it could still be usefull, and I haven't found an updated version

[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

---

