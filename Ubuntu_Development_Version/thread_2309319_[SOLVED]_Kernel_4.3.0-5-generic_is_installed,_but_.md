---
title: "[SOLVED] Kernel 4.3.0-5-generic is installed, but doesn't boot or seen"
date: 2016-01-09
forum: Ubuntu Development Version
---

### Post by Chanath on 2016-01-09
Kernel 4.3.0-5-generic is installed, but doesn't boot or seen; uname -a shows kernel 4.3.0-2-generic. Any upgrade or dist-upgrade is not helping. vmlinuz-4.3.0-5-generic is in /boot, not shown in grub also.

---

### Post by deadflowr on 2016-01-09
Are you dual-booting?

---

### Post by Chanath on 2016-01-09
> **deadflowr said:**
> Are you dual-booting?

Thanks pal, that was the problem. I let this system's grub to take over, and everything is good.:p

---

