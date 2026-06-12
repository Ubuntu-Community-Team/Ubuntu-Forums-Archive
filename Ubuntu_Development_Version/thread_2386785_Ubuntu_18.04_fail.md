---
title: "Ubuntu 18.04 fail"
date: 2018-03-10
forum: Ubuntu Development Version
---

### Post by cruzer001 on 2018-03-10
Been running on a fresh install (not a VM) for 3 days now.  This install has its own drive.

Today I fire it up and it goes straight to BusyBox.
Rescue Mode; straight to busybox.
No backup kernel, the install is too fresh.
Do I have any backup of this install?  Hell no :(

Guess I'll be doing a fresh install today.

---

### Post by vanadium on 2018-03-10
Well, this is not a stable version yet, after all.

---

### Post by cruzer001 on 2018-03-10
So your not going to tell me everything is going to be alright.

---

### Post by exploder on 2018-03-10
I went through something similar a week or so ago. That's the chance we take running a release that is still under development. Hopefully things will go our way the rest of this cycle.:)

---

### Post by ajgreeny on 2018-03-10
Try running fsck from a live system (the USB or DVD you used to install 18.04 will do) using command ```
sudo e2fsck /dev/sdx#
``` where sdx# is your root partition of the installed version.

You might be lucky or you might not but it certainly will not make matters worse so has got to worth a try.

---

### Post by cruzer001 on 2018-03-10
> **ajgreeny said:**
> Try running fsck from a live system (the USB or DVD you used to install 18.04 will do) using command ```
sudo e2fsck /dev/sdx#
``` where sdx# is your root partition of the installed version.

You might be lucky or you might not but it certainly will not make matters worse so has got to worth a try.

An excellent idea, but I have already reinstalled...next time.  Thanks

---

