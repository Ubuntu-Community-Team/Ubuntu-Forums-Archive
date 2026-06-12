---
title: "Vbox working fine, now not (kernel changes)"
date: 2009-04-18
forum: Virtualisation
---

### Post by EdwardD26 on 2009-04-18
So Ok I been running VBox with WinXP for a couple months now, everything working fine. Until today, I try to run my XP and says:

VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)


The VB Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing:

'etc/init.d/vboxdrv setup'


So I run that on the terminal and I get a permission denied error.

What should I do? What can I do? I havent really changed any settings on my XP/ununtu recently... why did this happend so randomly, cant event point to why this error shows up now, everything is theoretically the same as before.

Thanks

---

### Post by Shazaam on 2009-04-18
Did you put sudo in front of the command? Like so...
```
sudo etc/init.d/vboxdrv setup
```

---

### Post by EdwardD26 on 2009-04-19
omg cant believe it Im such a noob hahaha =)


This fixed it, wow so simple love ubuntu, thx Shazaam!

---

