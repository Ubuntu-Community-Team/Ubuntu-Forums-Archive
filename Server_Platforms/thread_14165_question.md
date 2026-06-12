---
title: "question"
date: 2005-02-05
forum: Server Platforms
---

### Post by haynest on 2005-02-05
I am trying to understand something in my logs

Jan 31 06:25:01 techweb CRON[20776]: (pam_unix) session opened for user root by (uid=0)
Jan 31 06:25:02 techweb su[20793]: + ??? root:nobody
Jan 31 06:25:02 techweb su[20793]: (pam_unix) session opened for user nobody by (uid=0)

Can someone explain what is going on here?

Cron daily runs at 6:25

---

### Post by gab10 on 2005-02-05
I think that's just a cron job dropping to run as nobody instead of root. I've seen it in other logs too, and I'm pretty sure that's all it is.

---

