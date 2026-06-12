---
title: "Need help fixing some broken dependencies"
date: 2006-08-27
forum: Repositories &amp; Backports
---

### Post by BongoBob on 2006-08-27
Hello everyone, I'm having some dependency issues here.

When I type sudo apt-get -f install, it says this...
```
bongobob@RaptorBandito:~/Desktop$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-4 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I belive that libc6 is the version I downloaded from the debian site (long story short I thought it was why easyh10 wouldn't install, still didn't work) instead of the actual ubuntu version, but when I type sudo apt-get remove libc6, it tells me that damn near everything depends on it and I can't remove it unless I remove them all.

Any way I can fix this? Thanks in advance.

EDIT: Nevermind, a friend of mine told me how to force it back to the ubuntu version :)

---

### Post by mssever on 2006-08-27
Here are two lessons I've learned the hard way: First, don't use the -f option. Second, if you ever try software that depends on something not available in an Ubuntu Dapper (or whatever your version is) repo, don't install it. Compile from source instead.

---

