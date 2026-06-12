---
title: "amd a10-4600m runs terrible"
date: 2012-09-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by deaconmacmillan on 2012-09-11
Im running a lenovo e435 with the a10-4600m trinity chip. when running the beta 1 with all updates I get black screen on boot untill running the nomodeset option in grub. also compiz takes about 80% of all 4 cpu cores. bleah...anyone having a better experience with similar hardware?

---

### Post by eandry on 2012-09-15
I confirm I have the same problem on my AMD Trinity Samsung laptop.
The bug is fixed in kernel 3.6-rc4. (Tested on my gentoo linux)
I don't know if the fix is planed to be backported to kernel 3.5

---

### Post by thotz on 2012-09-15
Found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1030216](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1030216)

---

### Post by deaconmacmillan on 2012-10-11
this issue seems to be largely rectified with the unity 6.8 release. everything is buttery smooth again. The black boot screen problem appears to still be present. nomodeset was still necessary last time I tried it.

---

