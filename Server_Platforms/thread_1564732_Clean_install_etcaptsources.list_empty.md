---
title: "Clean install: /etc/apt/sources.list empty?"
date: 2010-08-30
forum: Server Platforms
---

### Post by sleepyjon on 2010-08-30
During 10.04 install I ran into an error every time I tried to install packages, so I just skipped the step figuring I'd do it later.

Boot up, nothing but the cd in /etc/apt/sources.list. Does anyone know where I can find the default sources.list?:popcorn:

---

### Post by Bachstelze on 2010-08-30
```
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse

```

---

### Post by sleepyjon on 2010-08-30
Thank you!:D

---

