---
title: "Updating apache, mySQL, php, etc."
date: 2007-10-28
forum: Server Platforms
---

### Post by sonic99 on 2007-10-28
Well, for some reason the 7.10 server edition comes with outdated versions for all of these.  Running apt-get never seems to pick them up to be updated.

Problem is I have a couple sites already created and don't know how to upgrade without possibly screwing something up.  Can someone help?

---

### Post by dantrevino on 2007-10-28
If you have newer versions of these the reason they're not being "picked up" is because you didn't install them using the package manager.

Mixing packaged and unpackaged binaries can be done, but is not supported, and will inevitably lead to support issues.

Apache 2.2.6 is currently in Debian unstable if you wanna go that route.

dan

---

