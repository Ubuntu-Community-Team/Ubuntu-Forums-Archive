---
title: "Will the Linux kernal update mess with my wine?"
date: 2010-08-05
forum: Wine
---

### Post by DeadlyOats on 2010-08-05
I'm using Ubuntu 9.10.

Update Manager is showing me a new Linux kernel update: 2.6.31-22.

If I go through with the update, will it mess with my Wine 1.2 (installed from the Ubuntu repositories via Synaptic Package Manager)?

---

### Post by snowpine on 2010-08-05
The kernel update should be safe, shouldn't mess with any of your applications (like Wine).

Worst case scenario, let's say you don't like the new kernel, your old kernel will be available in the GRUB boot menu.

---

### Post by DeadlyOats on 2010-08-05
Wine translates from Linux to Windows, and from Windows to Linux.  So, a change in the kernel will have no adverse effects on how Wine translates something?

---

### Post by cogadh on 2010-08-05
Absolutely not, the kernel updates do not affect how Wine works. The only updates that ever affect how Wine works are Wine updates.

---

### Post by DeadlyOats on 2010-08-05
Thank you, snowpine and cogadh, for your quick replies.  Then, I shall go ahead with the kernel update.

Thanks again.

---

### Post by hikaricore on 2010-08-05
> **cogadh said:**
> Absolutely not, the kernel updates do not affect how Wine works. The only updates that ever affect how Wine works are Wine updates.

Actually this is only partially true.
Awhile back there was a kernel bug that affected the way that certain functions worked.
This in turned affected WINE and broke atleast two games.
Upon updating to a kernel which fixed this bug the issue disappeared.

While it is incredibly unlikely that a kernel update will affect WINE, it is atleast in some rare instances possible. ;)

---

### Post by dardack on 2010-08-05
> **hikaricore said:**
> Actually this is only partially true.
Awhile back there was a kernel bug that affected the way that certain functions worked.
This in turned affected WINE and broke atleast two games.
Upon updating to a kernel which fixed this bug the issue disappeared.

While it is incredibly unlikely that a kernel update will affect WINE, it is atleast in some rare instances possible. ;)

This.

---

### Post by cogadh on 2010-08-05
However, the fact still is, a kernel update will not directly impact Wine's functionality in any way. The only thing that might happen, **if** there is a significant bug in the kernel, is a change in the way the entire system works, not a change in the way Wine works.

---

