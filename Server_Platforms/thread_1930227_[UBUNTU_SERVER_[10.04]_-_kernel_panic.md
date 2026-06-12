---
title: "[UBUNTU SERVER [10.04] - kernel panic"
date: 2012-02-23
forum: Server Platforms
---

### Post by matijaz74 on 2012-02-23
Hi!
I have a problem when running the server. The problem has already occurred when I upgraded the kernel. The server is not run GRUB and freezes. 
Displays the error:```
kernel panic not syncing: vfs: unable to mount root fs on unknown-block (0,0)
```
How to fix it? Thanx for answer and help.

Matijaž

---

### Post by roelforg on 2012-02-23
Boot into a live-cd and post the output of:
```

sudo ls -la /dev/sd*

```

---

