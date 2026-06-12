---
title: "Update-initramfs refresh only default kernel"
date: 2019-01-25
forum: Ubuntu Development Version
---

### Post by zika on 2019-01-25
Udate-initramfs started refreshing only {running, instaled last, default in Grub (did not investigate deeper yet, bet on installed last)} kernel, not all, as it used to be. Not a big deal but just to warn those, like myself, who have more than one kernel active... It might be just a temporary thing, we will see.

---

### Post by Doug S on 2019-01-25
zika, thanks for the heads up. I had not noticed, but will pay attention going forward.

---

### Post by zika on 2019-01-27
> **Doug S said:**
> zika, thanks for the heads up. I had not noticed, but will pay attention going forward.Confirmed while transitioning/adding proposed repository. I will try to remember if that was default earlier and, if so, how it was possible to change that to „all“...
Update&#8321;: Silly old man that forgets too easily I am. File is  **/etc/initramfs-tools/update-initramfs.conf **&#8203;line is ```
update_initramfs=yes
```and should be```
update_initramfs=all
```Done...

---

