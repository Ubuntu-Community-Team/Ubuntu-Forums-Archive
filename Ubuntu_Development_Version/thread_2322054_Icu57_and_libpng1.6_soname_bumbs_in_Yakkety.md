---
title: "Icu57 and libpng1.6 soname bumbs in Yakkety"
date: 2016-04-26
forum: Ubuntu Development Version
---

### Post by harry332 on 2016-04-26
Yakkety package upgrading started with somewhat big soname bumbs:
icu55 => icu57
libpng => libpng1.6

To accomplish this, a number of packages depending on those need to be rebuilt.

Also, if someone has enabled Gnome3-Staging PPA and installed new Gnome 3.20 (Xenial branch),
certain packages need to be downgraded (to official Yakkety) due to soname bumbs,
like "evolution-dataserver", "tracker", "webkit2gtk".
This, however, will not cause any issues and Gnome 3.20 works fine now.

We are still waiting for at least rebuilt mplayer and gimp to finish the libpng1.6 soname bump.

---

