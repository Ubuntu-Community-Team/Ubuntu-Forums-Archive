---
title: "Blank screen on boot, possibly due to a swap file problem"
date: 2010-09-30
forum: Server Platforms
---

### Post by fzaker on 2010-09-30
Hi experts,
After several months of working without any problem, suddenly my server stopped working. When booting, a blank screen with cursor blinking is shown until ctrl-alt-del is pressed. In that blank screen any character typed by keyboard is shown, but no progress occurs after even several hours.
Holding shift button in grub menu and selecting recovery mode, causes some logs to be shown and every thing freezes after showing the following line:
```
[    8.321388] Adding 5853176k swap on /dev/mapper/mch-swap_1. Priority:-1 extents:1 across:5853176k
```My platform: Ubuntu Server 10.04 64bit, HP DL380G6, RAID 0, 4GB RAM

Any help is appreciated. I don't know how to diagnose the problem.

---

