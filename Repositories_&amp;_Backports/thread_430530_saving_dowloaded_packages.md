---
title: "saving dowloaded packages"
date: 2007-05-02
forum: Repositories &amp; Backports
---

### Post by mizar001 on 2007-05-02
Hi. I have to install some packages every time i re-install ubuntu, and i dowloaded those packages through the add/remove program or aptitude (synaptic etc.).

But there's a way to avoid the need of a high band internet connection and the need to downloading every time gigabytes of the same things? There's a way to save packages to a local (say a DVD-R)   repository ?

Thanks in advance.

---

### Post by Rui Pais on 2007-05-02
Hi, 
packages are saved at /var/cache/apt/archives/
you can make a copy of those to a somewhere or to some media.

I usually make that folder a link to a folder (dapper, edgy, feisty) inside a partition (that i formated as xfs, cause packages can be big) and with different installs i have always those available cause they are not deleted with partitions formats.

Or you can save them to a cd or dvd and add tha media to /etc/apt/sources.list *a posteriori* .

---

### Post by paparucino on 2007-05-02
> **Rui Pais said:**
> 

Or you can save them to a cd or dvd and add tha media to /etc/apt/sources.list *a posteriori* .

Try aptoncd. It saves all the .deb you dowloaded

---

