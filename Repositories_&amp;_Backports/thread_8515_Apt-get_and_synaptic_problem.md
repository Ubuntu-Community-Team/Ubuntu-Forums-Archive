---
title: "Apt-get and synaptic problem"
date: 2004-12-18
forum: Repositories &amp; Backports
---

### Post by ibs on 2004-12-18
When i try to install something using apt-get and Synaptic, i get this error:

```

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 10608 package `python-pyorbit':
 field name `!' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
ibs@ubuntu:~ $

```

This happens to every package i try to install. I'm a newbie to Linux so i can't figure this out myself.

---

### Post by ibs on 2004-12-18
nevermind, the problem is solved. I removed ! in that line in the file

---

