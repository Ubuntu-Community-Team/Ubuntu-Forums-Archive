---
title: "Repository Info - Report non-working repositories"
date: 2006-08-03
forum: Repositories &amp; Backports
---

### Post by greenstar on 2006-08-03
With the current spate of problems with repositories, I've been doing a little troubleshooting.

I've been disabling & then one-by-one reenabling suspect repositories, and have found that the dapper backports repo is currently not available.

So I propose that when you find a repository down, take note of which repo and post the corresponding line(s) (as in individual line(s), not the whole sources.list). This might help reduce the number of similar posts related to the same repository.


Example:

Today I found the dapper backports repository down:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

Greenstar

---

### Post by ciscosurfer on 2006-08-03
I don't mean to split hairs, but that's actually 8 repos (main, restricted, universe, and multiverse...times 2 because you've listed the deb-src file lines as well).

Try [some mirrors]("https://wiki.ubuntu.com/Archive").

---

### Post by greenstar on 2006-08-03
> **ciscosurfer said:**
> I don't mean to split hairs, but that's actually 8 repos (main, restricted, universe, and multiverse...times 2 because you've listed the deb-src file lines as well).

You're right, it didn't even cross my mind to think about that.:mrgreen: Looking back at my post, I see I did use the singular form "repo". 

> **ciscosurfer said:**
> Try [some mirrors]("https://wiki.ubuntu.com/Archive").

Thanks, ciscosurfer. Good link. Seems like there's another useful document or page on the wiki or something every time I turn around. I have dozens of excellent links for Ubuntu, but it never ceases to surprise me how much good info I still haven't found.

Greenstar

---

### Post by greenstar on 2006-08-04
On second, or maybe third thought... This is probably not as useful as I initially thought. Kind of like aiming for a moving target. I got my repos working anyway, so maybe things have been corrected server-side also.

Anyway, so much for the half-baked idea.

Greenstar

---

