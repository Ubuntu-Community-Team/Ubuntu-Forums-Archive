---
title: "Ubuntu ID through SSH... all  versions."
date: 2011-07-24
forum: Server Platforms
---

### Post by NetDoc on 2011-07-24
I am sure that this is a simple fix, but how do you figure out which Ubuntu you are running through ssh? Can I easily figure out if I have 10 or 11?

---

### Post by brighty22 on 2011-07-24
```
cat /etc/lsb-release
```

---

### Post by NetDoc on 2011-07-24
> **brighty22 said:**
> ```
cat /etc/lsb-release
``` Thanks!!! That was easy enough! ```
pjmu@epsilon:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS" 
```

---

### Post by Gyokuro on 2011-07-25
cat /etc/issue

---

