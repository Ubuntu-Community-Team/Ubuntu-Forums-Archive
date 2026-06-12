---
title: "Multi/Broadcasting console commands through servers"
date: 2009-09-08
forum: Server Platforms
---

### Post by jersak on 2009-09-08
I would like to know if theres any means of broadcasting a console/shell/bash command among several servers at once.
Like i type an useradd command, for instance, in server A and it does the same command at server "B" and "C" at the same time.

Thanks in advance.

---

### Post by HermanAB on 2009-09-08
There are at least two versions of Parallel SSH (e.g. pssh).  These systems are designed for managing clusters or identical corporate setups.  Some Googling will find it, and pssh may be in the repos already.

---

### Post by samosamo on 2009-09-08
Webmin does this and it does it well.

---

