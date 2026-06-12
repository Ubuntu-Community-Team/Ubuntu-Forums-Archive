---
title: "Unable to install wine with fglrx on 14.10"
date: 2014-10-11
forum: Ubuntu Development Version
---

### Post by n-fit-8 on 2014-10-11
On a fully updated system (amd64) i am unable to install wine, as doing so removes the fglrx drivers (installed with apt-get, problem with both fglrx and fglrx-updates). If i switch to the open source drivers, wine installs normally , however the whole point of installing wine (for me) is running games in which the proprietory driver sadly is faster. I dont believe that the driver is actually conflicting with wine but simply there is some packaging error (hopefully). 


PS: As i am mostly a forum lurker and this is my first post here in some years, i have no idea what logs/ info you might want so please dont scream at the noob :P

---

### Post by bjherbison on 2014-10-12
Updating Ubuntu and keeping wine has been a problem for some people for a while. Some people lost wine when upgrading to 14.04. (My current best hope is to get it back when upgrading to 14.10, but your post diminishes that hope.)

[https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1313123](https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1313123) (closed as dupe of [https://bugs.launchpad.net/ubuntu/+source/ocl-icd/+bug/1247736](https://bugs.launchpad.net/ubuntu/+source/ocl-icd/+bug/1247736)) mentions fglrx.
[https://bugs.launchpad.net/wine/+bug/1229221](https://bugs.launchpad.net/wine/+bug/1229221) is a similar issue.

---

### Post by n-fit-8 on 2014-10-12
:/ thanks anyways guess i'll have to build from source, or does it not work that way?

---

