---
title: "Creating a single repository from multiple DVD's"
date: 2007-01-17
forum: Repositories &amp; Backports
---

### Post by hexdream on 2007-01-17
Hi All,

I'm trying to create a single repository from multiple DVD disks, but am having trouble getting synaptic to see it.


I ran :

dpkg-scanpackages ./ /dev/null | gzip > Packages.gz

With the following output :

Wrote 20205 entries to output Packages file.

The output  file is 4.3MB.

I added the repo into synaptic as follows: 

file:/media/hdb4/test edgy restricted multiverse universe main

After doing the reload of packages, only the currently installed apps show.

What am I doing wrong?   ](*,)     :confused:

---

