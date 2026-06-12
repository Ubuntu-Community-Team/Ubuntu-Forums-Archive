---
title: "After resuming from suspend SD-Card read only"
date: 2014-04-07
forum: Ubuntu Development Version
---

### Post by daniel-holz91 on 2014-04-07
Resuming from suspend seems to cause my SD-Card - which I use as /home - to become read-only.

Sometimes it happens immediately after unlocking my tablet, sometimes it happens after a short amount of time but it always seems to be caused by suspend/resume.

Edit: Solved it by adding "mmc_core.removable=0" to grub boot options.

---

