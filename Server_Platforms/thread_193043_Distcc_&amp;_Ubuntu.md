---
title: "Distcc &amp; Ubuntu"
date: 2006-06-09
forum: Server Platforms
---

### Post by ManicMike on 2006-06-09
How do you make ubuntu use distcc when doing a sudo apt-get --build source?
Also where would I find the distcc hosts file?

---

### Post by brandt on 2006-06-28
I couldn't figure out how to set the apt-get/apt-build to use distcc.  As for your second question, you can add the line
```

DISTCC_HOSTS="localhost <other machines>"

```
in /etc/environment

if you also use ccache, you can also add
```

CCACHE_PREFIX="distcc"

```

---

