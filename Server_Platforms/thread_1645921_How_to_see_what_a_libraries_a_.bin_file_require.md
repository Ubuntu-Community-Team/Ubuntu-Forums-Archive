---
title: "How to see what a libraries a .bin file require"
date: 2010-12-15
forum: Server Platforms
---

### Post by chrislynch8 on 2010-12-15
Hi,

Is there a method to see what libraries a custom .bin file would require to run

---

### Post by WinstonChurchill on 2010-12-15
> **chrislynch8 said:**
> Is there a method to see what libraries a custom .bin file would require to run
If you're asking how to tell what libraries an executable loads, you do that with:
```
ldd *commandname*
```You can also see all the system calls an executable invokes with:
```
strace *commandname*
```

---

