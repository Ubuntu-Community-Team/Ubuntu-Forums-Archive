---
title: "PMP SRST CONFIG_SATA_PMP=n"
date: 2011-10-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2011-10-23
Is there a solution for```

ata1: softreset failed (device not ready)
``` with a long pause after that (during boot) other than recompiling kernel with CONFIG_SATA_PMP=n?...

---

### Post by Harry33 on 2011-10-23
Try powering off, cutting the power from the power source completely for a few seconds.
This helps often times when I have reset issues with the lan card.

---

### Post by effenberg0x0 on 2011-10-23
Since it seems to relate to a kernel incompatibility to some specific hw / ahci, it will continue to affect Ubuntu in all releases until something is changed in Kernel. There are reports and requests for fixes for this bug, but I don't believe they relate to PP in any way. And current reports are sparse.

If I were you I would check if the bug still exists on the latest daily build and RC. If so, I'd file a bug against Kernel with links from as many other bug reports and forum posts regarding this particular issue as possible linked to it. That would facilitate the work of bug triagers and validate your report, increasing the chances of having it looked at. 

Regards,
Effenberg

---

### Post by zika on 2011-10-24
> **effenberg0x0 said:**
> If I were you I would check if the bug still exists on the latest daily build and RC.It does...
Once I get enough spare time I'll file a bug...

---

### Post by zika on 2011-10-24
> **Harry33 said:**
> Try powering off, cutting the power from the power source completely for a few seconds.
This helps often times when I have reset issues with the lan card.Power is cut while I sleep. That should be enough, every night... ;)

---

### Post by zika on 2011-12-11
I think that &#8222;pci=nocrs&#8220; in kernel boot line cured this &#8222;problem&#8220;...

Update: No it did not... It would be strange if it would have...

---

### Post by zika on 2012-03-29
It seems that BIOS upgrade did the trick. I hope... ;)
Update: No it did not: ```
[    1.589945] ata1: applying PMP SRST workaround and retrying
[    1.590057] ata3: applying PMP SRST workaround and retrying
[   34.365430] ata3: applying PMP SRST workaround and retrying
[   74.316052] ata3: applying PMP SRST workaround and retrying
```
Searching...

---

