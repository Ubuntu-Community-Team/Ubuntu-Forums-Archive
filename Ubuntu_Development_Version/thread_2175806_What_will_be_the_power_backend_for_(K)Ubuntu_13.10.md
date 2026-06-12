---
title: "What will be the power backend for (K)Ubuntu 13.10?"
date: 2013-09-21
forum: Ubuntu Development Version
---

### Post by rohandhruva on 2013-09-21
I have Kubuntu 13.04 installed. KDE uses powerdevil to manage hibernate/sleep, which in turns seems to use pm-utils backend. pm-utils is unmaintained, and broken at this point[1]. For example, I had to jump through many hoops to just enable in-kernel hybrid suspend which has been present since kernel 3.6.

I asked on Freenode #kde, and it seems like KDE powerdevil has been modified to accept newer backends for a while now. The order of preference is roughly systemd-login1, upower, and Solid.

Does anyone know what power backed will *buntu 13.10 use?

[1]: The pm-utils code was last updated in 2010, and they have not been accepting patches.

---

