---
title: "Do different versions of ubuntu have different package repositories?"
date: 2007-10-19
forum: Repositories &amp; Backports
---

### Post by netimen on 2007-10-19
Why 7.10 contains for example emacs 22.1, but I can't install it on 7.04 (I mean via apt-get, wich says that 21.4a is the newest version). And there are many other examples. Is it because new versions of programs aren't added to the repository after system release?

---

### Post by renzokuken on 2007-10-19
yes, each version has their own repos.  i think a typical life cycle of a non-LTS release is 18 months so packages should be updated for 18 months after release, but no guarantees all packages will be the latest.

your best bet is to either compile the newer emacs from source, or request a **BACKPORT**

---

### Post by netimen on 2007-10-19
But why nit ti have a single repo for all distro's?

---

### Post by renzokuken on 2007-10-19
becuase it would be a nightmare to maintain, dependencies would conflict and kernel upgrades would break alot of stuff.

easier to manage a few smaller repos than one huge McDaddy one

---

### Post by netimen on 2007-10-19
yeah, understood, thank you

---

