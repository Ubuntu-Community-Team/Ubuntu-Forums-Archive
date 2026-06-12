---
title: "System cannot upgrade to 18.10 because of a bug in appstream"
date: 2018-09-21
forum: Ubuntu Development Version
---

### Post by wgarcia on 2018-09-21
Due to this bug that has been fixed in 18.10:

[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1785498](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1785498)

I cannot upgrade one of my 18.04 systems to the 18.10 development release (strangely I could upgrade another one without any problem). The details of the system I cannot upgrade are in this bug which has been duplicated to the previous one:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1793164](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1793164)

The main bug report is about another problem but there are a couple of messages and duplicated bugs that also report that this is blocking some 18.04 systems from upgrading to 18.10 (see message #9 in the first bug). I've asked the first bug to be nominated to "bionic" and to do a stable release update in 18.04 (as far as I can tell substituting the 18.04 version of "appstream" and "libappstream4" to the current stable upstream version fixes this without any other consequence), but no reaction so far.

---

### Post by wgarcia on 2018-09-24
This has been fixed and is being released soon to 18:10:

[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1792537](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1792537)

---

