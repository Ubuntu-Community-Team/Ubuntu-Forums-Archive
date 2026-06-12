---
title: "GNOME Calculator"
date: 2018-04-10
forum: Ubuntu Development Version
---

### Post by $yl9pAR%t on 2018-04-10
GNOME Calculator does't start. Anybody else has the same problem?

In terminal I get this:

```
dario@dario-EP31-DS3L:~$ gnome-calculator
failed to create prefix path: /tmp/snap.rootfs_04kqC0/var/lib/snapd/lib/vulkan/icd.d: Permission denied
```

---

### Post by dino99 on 2018-04-10
mine works (gnome-shell on xorg session)

---

### Post by exploder on 2018-04-10
Works here under Wayland too. Your system probably has the snap version and the regular package installed at the same time. Remove the 3.28 version with the package manager and it should work again.

---

### Post by $yl9pAR%t on 2018-04-10
Thanks for answers. In a few days I will install fresh system.

Edit:

Installing regular package resolved this issue.

---

### Post by duke7553 on 2018-04-10
Try running the command below:

[FONT=system]$ snap refresh --beta core[/FONT]

It worked for me. I had a problem opening the spotify snap with that same error message.

EDIT: Didn't see issue was resolved by OP. Hopefully, this benefits someone else.

---

