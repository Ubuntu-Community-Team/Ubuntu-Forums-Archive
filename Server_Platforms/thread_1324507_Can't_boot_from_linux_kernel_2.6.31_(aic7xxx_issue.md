---
title: "Can't boot from linux kernel 2.6.31 (aic7xxx issue)"
date: 2009-11-12
forum: Server Platforms
---

### Post by thantos on 2009-11-12
So I upgraded from 9.04 to 9.10.  Now, I can still boot from linux kernel 2.6.28 but when I boot from the 2.6.31
kernel I get errors from aic7xxx.  It drops me to busybox and prints something like this:
```

aic7xxx_abort returns 0x2002
```

It returns more information but I won't be able to get it till later (Can't bring the computer down for awhile).

Sorry about having so little info.

---

### Post by siucdude on 2010-01-30
Same issue here.  seems this does not work on the new kernel... still looking for alternatives.

---

### Post by siucdude on 2010-02-20
issue solved.  its a temp fix but it works wonders on scsi cards. when booting in grub, boot with options noapic & nolapic 

Thanks

TJ

---

