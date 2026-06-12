---
title: "HU:libgdk-pixbuf"
date: 2019-12-08
forum: Ubuntu Development Version
---

### Post by zika on 2019-12-08
It will sort &#8222;itself&#8220; soon, I hope... ;)```
:~$ apt list --upgradable -a
Listing... Done
libgdk-pixbuf2.0-0/focal-proposed 2.40.0+dfsg-1ubuntu1 amd64 [upgradable from: 2.40.0+dfsg-1build1]
libgdk-pixbuf2.0-0/focal,now 2.40.0+dfsg-1build1 amd64 [installed,upgradable to: 2.40.0+dfsg-1ubuntu1]
```Round the Robin...

---

### Post by harry332 on 2019-12-10
I think this is solved now, the packages are in the release pocket.
The issue was that the package libgdk-pixbuf2.0-common could not be found, though it was built OK.
I installed these 3 packages manually.

---

