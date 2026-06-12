---
title: "Medibuntu Warning"
date: 2007-09-29
forum: Repositories &amp; Backports
---

### Post by frogotronic on 2007-09-29
I'm getting a wierd medibuntu warning about duplicate packages listing:

here's my sources list (attached)

What's going on?

---

### Post by aysiu on 2007-09-29
These appear to be the duplicates: ```
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
``` Try getting a fresh sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

