---
title: "Best Location for web folders"
date: 2009-03-10
forum: Server Platforms
---

### Post by mistypotato on 2009-03-10
Good morning,

Should web folders and files be placed in **/www** or **/www/htdocs** ?

If one is preferred over the other, why ?

thx :KS

---

### Post by cdenley on 2009-03-10
Typically, web files go in /var/www. This is the directory used by default when you install apache. There isn't any reason except that is the most common directory, unless you used a more complicated partitioning scheme. Just make sure non-root users cannot modify the directory, or any directory higher in the hierarchy.

---

### Post by hyper_ch on 2009-03-10
I prefer to store all "important user data" on the same partition.

So I create a /data partition and

symlink /home to /data/home
symlink /var/www to /data/www
symlink /var/lib/mysql to /data/mysql

but that's only for servers. On the desktop I keep things as they are.

---

