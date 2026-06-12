---
title: "[SOLVED] How do I know the packages names?"
date: 2006-10-26
forum: Repositories &amp; Backports
---

### Post by saul_2110 on 2006-10-26
Hi. When using the apt-get, it needs the name of the package but how do I know the package name ](*,) ?
Also,if certain package is not listed neither in synaptic nor the sources.list repositories... does that mean I can't installed ](*,) ?
Thanks.

---

### Post by Jussi Kukkonen on 2006-10-26
**Package name:**
you probably know something about the package, so do a search. Example:
```
apt-cache search http server load balancing
```
[B]
Packages not in repositories:[/B]
You can only install packages that are available in the repositories you have enabled. If a package is not available, you have a couple of choices (in order of preference):
1. add a repository that has the package (unsupported ubuntu repositories or 3rd party repositories)
2. install from a .deb-package you download from somewhere
3. install with a binary installer or compile from source (downloaded from the net)

---

### Post by az on 2006-10-26
The simplest way to search for and install packages is the add-remove programs menu entry.

It will give you a full list of packages.  Enabling extra repositories is made easy (you just tick a box or two) and it installs packages just as any other package manager frontend.

---

### Post by saul_2110 on 2006-10-27
Thanks for your answers. 

But now, how do I add a repository? I tried to copy the address of a debian repository in the source.list but apt-get return an error.

---

### Post by az on 2006-10-27
> **saul_2110 said:**
> Thanks for your answers. 

But now, how do I add a repository? I tried to copy the address of a debian repository in the source.list but apt-get return an error.

Do not use debian repositories!  Debian and Ubuntu are not binary-compatible.


See here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

