---
title: "Removed VirtualBox, but the allocated space doesn't free up."
date: 2009-05-03
forum: Virtualisation
---

### Post by elgoog on 2009-05-03
I installed Virtual Box a week ago assigning 15gb for Windows Guest. I have removed it now.(Both using 'apt-get'). But the 15gb space I have assigned does not free up. Any idea on how this can be done?

---

### Post by emnaki on 2009-05-03
```

rm -r ~/.VirtualBox

```

---

### Post by elgoog on 2009-05-03
Thank You Bro. Worked it out. I assume the same should be done for VMWare? Just delete the VMWare directory containing the .vmk files?

---

### Post by emnaki on 2009-05-03
Ye, thats right, assuming you want to remove VMWare completely.

---

