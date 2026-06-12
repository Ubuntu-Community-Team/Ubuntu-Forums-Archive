---
title: "Slow Transfer?"
date: 2009-07-13
forum: Ubuntu One (CLOSED)
---

### Post by RealG187 on 2009-07-13
This morning I had to send a few files up from my laptop, but it took quite a while...

Is the server slow because of high demand or something?

---

### Post by pfibiger on 2009-07-14
Hi,

You can run:

u1sdtool --current-transfers

which will show you how many files Ubuntu One has synced and how many are left. Perhaps you've got more files that need to sync than you realize. You can also look at your network monitor gnome applet and see what % of your upstream bandwidth is being used. It should be using as much of your upstream bandwidth as it can.

---

### Post by xinix on 2009-07-16
My upload is incredibly slow.  And it's not a bandwidth limitation on my end.   It looks like it's going to take several hours to send 10Meg.

---

### Post by RealG187 on 2009-07-16
My entire folder is only 4 MB

---

