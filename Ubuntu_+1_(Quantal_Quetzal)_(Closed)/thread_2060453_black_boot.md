---
title: "black boot"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by lucazade on 2012-09-20
after the latest updates I get a black screen during bootup... it seems related to the vt.handoff=7 feature of grub.
Infact removing this I can see at least the virtualterminal during bootup.
Maybe it is not correctly patched the latest release of grub (2.00-5ubuntu1)

anyone get the same? 

opened this bug-report:
[https://bugs.launchpad.net/ubuntu/+s...2/+bug/1053269](https://bugs.launchpad.net/ubuntu/+s...2/+bug/1053269)

---

### Post by 67GTA on 2012-09-20
I am getting this today after updating. The plymouth theme is there, but the screen is almost black. The bug report you linked to says "Page Not Found".

---

### Post by krack3rz on 2012-09-20
> **lucazade said:**
> after the latest updates I get a black screen during bootup... it seems related to the vt.handoff=7 feature of grub.
Infact removing this I can see at least the virtualterminal during bootup.
Maybe it is not correctly patched the latest release of grub (2.00-5ubuntu1)

anyone get the same? 

opened this bug-report:
[https://bugs.launchpad.net/ubuntu/+s...2/+bug/1053269](https://bugs.launchpad.net/ubuntu/+s...2/+bug/1053269)


lucazade meant this: [https://bugs.launchpad.net/ubuntu/+bug/1053269](https://bugs.launchpad.net/ubuntu/+bug/1053269)

for some reason it cuts out: +source/grub2  (too long?)
and without it works like a charm

---

### Post by lucazade on 2012-09-20
yep.. i meant that link but i pasted it wrong :P

---

### Post by thotz on 2012-09-21
Yes I also have this problem.

---

### Post by consolation on 2012-09-21
When it hits black screen, hit alt-f6 (or f5? whatever the active console is) it brings up the bootscreen with option to continue. For me anyway...

---

### Post by lucazade on 2012-09-21
reverting to -21 kernel fixes the issue..

---

### Post by lucazade on 2012-09-25
fixed with kernel 3.5.0-15.23!

---

