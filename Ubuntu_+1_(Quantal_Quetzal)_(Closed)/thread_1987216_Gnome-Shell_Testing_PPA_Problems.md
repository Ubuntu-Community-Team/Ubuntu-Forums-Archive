---
title: "Gnome-Shell Testing PPA Problems"
date: 2012-05-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ricotz on 2012-05-26
Regarding the usage of ppa:ricotz/testing, there are some difficulties due premature version bumps in my ppa. So please downgrade all your cogl packages to versions of 0.10.3+ in your preferred way/package-manager. A run of ppa-purge and re-adding the ppa should work too. 

So make sure there are no cogl packages with a 1.11.x version!
gir1.2-cogl-1.0, gir1.2-coglpango-1.0, libcogl-common, libcogl-dev, libcogl-doc, libcogl-pango-dev, libcogl-pango0, libcogl-pango0-dbg, libcogl9, libcogl9-dbg
Currently it is 1.10.3+git20120524.cb5efc11

Sorry for the inconveniences,
Rico

---

### Post by kansasnoob on 2012-05-27
Thanks for taking the time to let us know :)

---

