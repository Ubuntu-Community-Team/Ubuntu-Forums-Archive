---
title: "Breezy extras?"
date: 2006-01-31
forum: Ubuntu Backports
---

### Post by vaskark on 2006-01-31
Can someone list the repository of the breezy-extras category? Thanks. Also, is there a concise list of all the official ubuntu repositories somewhere? I just want to know if there are any I'm currently missing. I'm only interested in repos from the ubuntu servers/mirrors.

Thanks!

---

### Post by pertti on 2006-02-01
As far as I know, there is no breezy-extras respository, just the usual ubuntu, universe and multiverse repositories, plus breezy-backports. This is the apt-get line for the backports:

```
deb http://archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted
```

---

