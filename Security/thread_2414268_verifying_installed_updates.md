---
title: "verifying installed updates"
date: 2019-03-07
forum: Security
---

### Post by cam17 on 2019-03-07
Can I re-verifiy the already installed updates on a Ubuntu station??  My workstation crashes only after I install updates so I am suspecting that one or more updates is causing a problem.

---

### Post by TheFu on 2019-03-08
You can reinstall the packages using **sudo apt install --reinstall {pkgname}** This will re-validate the crypto-signatures of the package.
However, I would check the system log files for clues.  The logs almost always show the cause of any error so either a software or config or hardware solution can be found.

---

