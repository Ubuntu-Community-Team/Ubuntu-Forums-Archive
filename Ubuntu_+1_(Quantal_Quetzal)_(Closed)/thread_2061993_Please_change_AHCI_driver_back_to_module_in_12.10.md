---
title: "Please change AHCI driver back to module in 12.10"
date: 2012-09-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Tony Hung on 2012-09-23
AHCI is build-in kernel since 12.04, but our customer is need to install our software RAID AHCI module support for ubuntu. Although We found a method to unbind original AHCI , but still hope you can change AHCI driver back to module in 12.10. Thank you. Tony Hung

---

### Post by cariboo on 2012-09-23
You'll probably have more luck reporting your problem as a bug, as the kernel developers rarely read the forums. If you don't have an account on [Launchpad]("https://launchpad.net/"), you'll have to create one, then from the desktop of a system running Quantal (12.10) either open a terminal, or press Alt-F2 and type:

```
ubuntu-bug linux
```

and explain your problem in as much detail as possible.

---

