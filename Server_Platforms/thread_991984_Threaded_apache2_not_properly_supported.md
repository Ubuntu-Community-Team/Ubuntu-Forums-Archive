---
title: "Threaded apache2 not properly supported?"
date: 2008-11-24
forum: Server Platforms
---

### Post by wyldfury on 2008-11-24
Hi,

I've been moving existing servers to Ubuntu over the last year. I've now wanted to do an web server, only to find that Ubuntu doesn't have much in the way of packages supporting threaded apache.

There's an apache-mpm-worker package, but simple things like phpmyadmin require apache-mpm-prefork. Are there any plans to make packages for php5/phpmyadmin (and the various other extras) that will work with the worker mpm?

I'd have thought worker would have been preferential for servers as it's supposed to provide improved performance over prefork. That and having to maintain php5 from source with all the extras (mysql etc) is likely to be a giant pain in the ***.

Cheers
Guy

---

### Post by CrucifiedEgo on 2008-11-24
The problem is, PHP is not entirely thread safe(the core is, but many modules aren't), which is why some packages require the prefork module.  I don't know that there's much you can do in this case, other than compile the latest PHP often and only use threadsafe libraries.

---

