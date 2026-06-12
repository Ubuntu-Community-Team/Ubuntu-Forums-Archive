---
title: "Bug on radiance theme."
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by serdotlinecho on 2012-09-20
Hi, i'm using radiance theme, but the window theme is using ambiance theme.

---

### Post by nilarimogard on 2012-09-21
That's because gtk-window-decorator doesn't use  GSettings. This was fixed in Compiz from the proposed repository so if you enable this repo, you'll get the fix...

---

### Post by serdotlinecho on 2012-09-21
After update and upgrade, now it's looking good again, thank you. :p

---

