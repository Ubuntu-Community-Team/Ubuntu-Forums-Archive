---
title: "Daily build install: Getting &gt; Warning: Fake initctl called, doing nothin"
date: 2012-01-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2012-01-31
Any ideas. I can chroot in. The installer did crash with the flash bug right at the end.

---

### Post by dino99 on 2012-01-31
funny idea, maybe you can try to install with --flash

---

### Post by philinux on 2012-01-31
> **dino99 said:**
> funny idea, maybe you can try to install with --flash

I fixed up the sources list and did a dpkg --configure -a and flash sorted it self out. It just wont boot. I get the error message in recovery mode when I try to resume normal boot.

The install may be borked. Might have to reinstall it without the extras.

---

### Post by dino99 on 2012-01-31
> **philinux said:**
> I fixed up the sources list and did a dpkg --configure -a and flash sorted it self out. It just wont boot. I get the error message in recovery mode when I try to resume normal boot.

The install may be borked. Might have to reinstall it without the extras.

yes reinstall flash later

---

### Post by philinux on 2012-01-31
Ok now. Typing from precise. Reinstalled without extras. But.

It would not boot from normal kernel. Had to use recovery mode but it went to login. Weird. Logged in and installed nvidia-current from jockey and all's well.

---

