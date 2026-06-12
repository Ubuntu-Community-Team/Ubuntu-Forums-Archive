---
title: "Want to move from apt-mirror to rsync"
date: 2014-07-29
forum: Server Platforms
---

### Post by trekkiejonny on 2014-07-29
I am currently using apt-mirror to download package in preparation for making a local repository. I would like to switch to using rsync. How do I do this where I only download Precise + Trusty and not every release that has come before and after? Also would like to mirror Debian 7.0 Wheezy. Ive asked this question before 7 months ago on [AskUbuntu]("http://askubuntu.com/questions/396236/rsync-mirror-specific-ubuntu-distributions"). So if you want to answer me on there for the reputation points that would be perfectly alright.

---

### Post by TheFu on 2014-07-29
I use **apt-cacheng** - don't know if that is the same. It only mirrors the things I load, nothing else.  It supports any APT distro, PPA, repository.  Are you sure you want to mirror everything?

---

### Post by trekkiejonny on 2014-07-29
That's a good suggestion but I am looking into mirroring a whole release repository. However I may use that for working with other Debian distros.

---

