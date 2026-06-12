---
title: "how to get return address from fast system call (sysenter)?"
date: 2008-06-08
forum: Security
---

### Post by RaistlinU on 2008-06-08
[FONT="Arial"]Does anyone know how to get return address of system call when it's a fast system call? When I look at regs.eip, I always get 0ffffe410. I searched for some info, it says there is no push/pop stack operation during FSC. Then from where I can get the return address when a system call happens? My kernel is 2.6.22.9.
Many thanks in advance.[/FONT]

---

