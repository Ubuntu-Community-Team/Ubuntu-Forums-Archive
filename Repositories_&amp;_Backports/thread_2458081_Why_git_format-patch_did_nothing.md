---
title: "Why git format-patch did nothing?"
date: 2021-02-15
forum: Repositories &amp; Backports
---

### Post by jimhce on 2021-02-15
Hi,

I am running two laptop one is ubuntu 18.04, another is 20.04,  I made changes in a git source, the patch files are in patches directors, but when I run git format-patch, it did nothing, it supposed to write cover letter to each patch files, it did not. What I get wrong there?

 $ git format-patch  --cover-letter origin/master -o patches

It did not write anything to patch files in patches directory.

---

