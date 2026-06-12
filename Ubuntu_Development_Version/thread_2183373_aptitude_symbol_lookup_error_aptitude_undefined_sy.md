---
title: "aptitude: symbol lookup error: aptitude: undefined symbol: _ZNK7tagcoll4coll4FastISsS"
date: 2013-10-24
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2013-10-24
Seems to be this bug:

[http://permalink.gmane.org/gmane.linux.debian.devel.bugs.rc/389394](http://permalink.gmane.org/gmane.linux.debian.devel.bugs.rc/389394)

[http://osdir.com/ml/general/2013-10/msg47642.html](http://osdir.com/ml/general/2013-10/msg47642.html)

```
paul@trusty-64:~$ apt-cache search libept
libept-dev - High-level library for managing Debian package information
libept1.4.12 - High-level library for managing Debian package information
goplay - games (and more) package browser using DebTags
paul@trusty-64:~$
```

```
paul@trusty-64:~$ apt-cache policy libept1.4.12
libept1.4.12:
  Installed: 1.0.10
  Candidate: 1.0.10
  Version table:
 *** 1.0.10 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.0.9 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
paul@trusty-64:~$
```

```
paul@trusty-64:~$ apt-cache policy libept-dev
libept-dev:
  Installed: (none)
  Candidate: 1.0.10
  Version table:
     1.0.10 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-proposed/main amd64 Packages
     1.0.9 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
paul@trusty-64:~$
```

Relying on apt-get until it's fixed.

---

### Post by paul_in_london on 2013-10-24
Fixed with this update:

```
paul@trusty-64:~$ apt-cache policy libept1.4.12
libept1.4.12:
  Installed: 1.0.12
  Candidate: 1.0.12
  Version table:
 *** 1.0.12 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     1.0.9 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
paul@trusty-64:~$
```

---

