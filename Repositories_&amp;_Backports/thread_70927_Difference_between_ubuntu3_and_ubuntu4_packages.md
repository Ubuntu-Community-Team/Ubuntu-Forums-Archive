---
title: "Difference between ubuntu3 and ubuntu4 packages"
date: 2005-10-01
forum: Repositories &amp; Backports
---

### Post by sebast on 2005-10-01
Can someone tell me the difference between these two packages for exemple:

0.8.11-0ubuntu3 and 0.8.11-0ubuntu4

Thanks

---

### Post by UbuWu on 2005-10-01
The first version number is the version of the upstream source (the original program source). The ubuntu version number is the Ubuntu package version number. Every time something is changed to the package (dependencies changed, etc.) this number is increased by one.

---

### Post by jdong on 2005-10-01
As UbuWu said, the ubuntu4's are newer than Ubuntu3's.

The versioning scheme is used to reference upstream (Debian Sid) package versions. The full format is:

packagename_version-X[ubuntuY]

For example, let's take firefox as an example. Say that Firefox 1.5 is released today. Debian Experimental, being the on-the-ball packagers they are, will make a Firefox package:

firefox_1.5-1

Note that this is the first Debian revision (that's what the -1 means). Now, Ubuntu wants it. If Ubuntu directly imports this package from Debian, it'd be named identically as Debian's version. However, realistically most major desktop packages benefit from Ubuntu patches, such as fancy Cairo graphics or Launchpad integration. As a result, Ubuntu takes the Debian version, and adds a bit more to it. It's released as:

firefox_1.5-1ubuntu1

If this is found to have bugs or need even more patching, subsequent revisions would have ubuntu2, ubuntu3, ubuntu4, and so on. Security updates would append ".1, .2, .3", and so on to the entire version string.


Now, let's say that GAIM 2.0 is released today, but the Debian GAIM maintainer is taking a vacation. Ubuntu probably would go ahead and make the package. Since the package didn't exist in Debian, "1ubuntuX" would be implying a Debian revision, so we need a 0 instead of 1. For example:

gaim_2.0-0ubuntu1

would be the first revision of GAIM. Later, if Debian releases their GAIM packages, Ubuntu and Debian would likely resync, and thus 1ubuntu1 would be born :)

---

