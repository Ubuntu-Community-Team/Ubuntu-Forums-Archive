---
title: "Astrolog 5.40-3"
date: 2007-05-19
forum: Ubuntu Backports
---

### Post by Oceola on 2007-05-19
I recently downloaded this from the Debian archives and had some minor success installing it. It seems to work for some things and not others due to a partial install.
Biggest issue is there is not a complete install due to the "dependency" on the  "plain wrapper" Debian Libc6 Version and though parts of it work with the Ubuntu Libc6 and the Libc6-686 for the partial install.
It closes the Xserver when using some of the Graphic chart display because of the incomplete install..
I have been unable to find a version in the US, GB or ?Multiverse archives.
This Debian version has been released for testing and does not have a maintainer.
It may be a simple matter of modifying the software to recognize the Ubuntu Dapper version's named Libc6 at installation. So far it has been calculating a number of functions properly.
Gdebi recognized the dependency and would no allow the install, dpkg recognized the dependency and performed a partial install.

Would really like to see this in the Dapper Multiverse or some repository somewhere?

Thanks

---

