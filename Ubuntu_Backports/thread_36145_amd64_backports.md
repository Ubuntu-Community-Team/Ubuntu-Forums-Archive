---
title: "amd64 backports"
date: 2005-05-22
forum: Ubuntu Backports
---

### Post by micolous on 2005-05-22
I'm fed up with the lack of amd64 packages, and want to do something about it.  I've had a quick look at the package building cheatsheet, and I was wondering if there was a nice way to build the packages en masse, so that I could just have a script running during the early hours of the morning or while I'm out that will build all the packages.  I'm currently slowly checking out a copy of the SVN repository.

---

### Post by jdong on 2005-05-22
Script: not that I know of. At least half of the packages have to be manually tweaked, either via build dependencies or actual patching, or applying older diffs to newer packages.


If you'd like to be an amd64 developer and get access rights to the repository, please contact me.

---

