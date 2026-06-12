---
title: "usplash improvements"
date: 2008-05-16
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2008-05-16
The "progress bar" should be fully "smooth" in its movements.

To achieve this I suggest timing how long a boot takes on first boot, integrating that result into the initramfs during the first kernel update (where it would be regenerated anyway), and then smooth scrolling the progress bar based on that timing.

(so if a system takes 20 secs to boot, after 5 secs the progress bar is at 25%, after 10 secs it's at 50% etc.)

---

