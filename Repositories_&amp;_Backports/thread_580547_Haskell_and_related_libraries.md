---
title: "Haskell and related libraries"
date: 2007-10-18
forum: Repositories &amp; Backports
---

### Post by Othersider on 2007-10-18
Hi,

I just upgraded to Gutsy Gibbon.  It automatically upgraded the ghc6 package for me, but it seems like there are not updated packages for most, if not all, associated libraries.  Specifically, I get the following error when I try to install soegtk:

> libghc6-soegtk-dev:
  Depends: ghc6 (<6.6+) but 6.6.1-2ubuntu2 is to be installed
 Depends: libghc6-gtk-dev but it is not going to be installed
 Depends: libghc6-cairo-dev but it is not going to be installed

How can I fix this?  The bug is documented [here]("https://bugs.launchpad.net/ubuntu/+source/ghc6/+bug/129050"), but I need to fix it for a course as soon as possible and would really appreciate help.

In other words...is there any way I can downgrade a specific package to its feisty version?

Thanks!

---

### Post by Othersider on 2007-10-23
Let me clarify/bump, because I think Haskell in the subject scared people away.  This question really does not have anything to do with Haskell:

**Is there a way I can install packages from previous version of Ubuntu (ie. Feisty)?**

Thanks again.

---

