---
title: "phpMyAdmin removes apache2-mpm-worker"
date: 2009-11-03
forum: Server Platforms
---

### Post by aajax on 2009-11-03
I'm trying to setup phpMyAdmin on Ubuntu Server (Hardy).

The Debian installation is poorly described.  However, it seems installing the phpMyAdmin package on a server that is running apache2 with the apache2-mpm-worker has the affect of removing it and installing apache2-mpm-prefork.

There is no mention of any such apache requirements in any phpMyAdmin documentation that I can find, which leaves me very perplexed.  I do want to use mpm-worker.

Can anyone explain what's going on here?

---

### Post by aajax on 2009-11-04
A little further research reveals that it is PHP that recommends avoiding the use of a multi-threaded MPM. They seem to be suggesting that while their code is thread safe PHP depends on many other libraries where that may not be the case.

---

