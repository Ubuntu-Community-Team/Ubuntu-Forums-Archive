---
title: "&quot;bin/kmod&quot; error while installing nvidia drivers on encrypted drive"
date: 2013-03-12
forum: Ubuntu Development Version
---

### Post by Juniorr on 2013-03-12
When installing nvidia drivers on an encrypted drive, system reports an error on /bin/kmod.

How does that affect on the driver itself? Because I tried running a system test only selected the graphics test and it failed.

---

### Post by Juniorr on 2013-03-13
Bump

---

### Post by dino99 on 2013-03-13
except that warning, there is nothing scary, the driver works
lp :1073062

---

### Post by Juniorr on 2013-03-13
How to be 100% sure? When "System Test" was made it reported an error on Graphics Test. If kmod failes to register the kernel module on encrypted systems, why add both options togeter?

---

### Post by wgarcia on 2013-03-14
This is a known bug that has been already "fixed released", should be landing in raring in an update any time now:

[https://bugs.launchpad.net/ubuntu/+source/kmod/+bug/1073062](https://bugs.launchpad.net/ubuntu/+source/kmod/+bug/1073062)

---

