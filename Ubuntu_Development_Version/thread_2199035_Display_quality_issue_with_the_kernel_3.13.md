---
title: "Display quality issue with the kernel 3.13"
date: 2014-01-11
forum: Ubuntu Development Version
---

### Post by Yahoé on 2014-01-11
Kernel 3.13.0..2.5 got pushed from the official repository following 3.13-0-1.
With these two kernel iterations, the display  quality is just unbearable (HDTV) on a system with a Radeon HD 4200 series,  bad resolution, dark, colours totally off. I  had to switch back to  3.12.0-7-generic which instantly fixes the issue.

Is anyone else experience a similar problem?

---

### Post by d-cosner on 2014-01-11
I have not seen any display issues using the open source drivers with an ATI Radeon HD 5775 and the 3.13 kernels.

---

### Post by Yahoé on 2014-01-12
Thanks for your input -dcosner. I just tried booting from the latest ubuntu daily live, and the display quality problem is there right from the start. So it's not coming form my install, but something has changed enough in this new kernel to mess up the way my system works. I'll just wait to see if get ironed out in the near future. I'll stick to kernel 3.12.0-7 in the meantime since this one works nicely.

---

### Post by rtalcott on 2014-01-12
I am running Xubuntu 3.13-0-2 on a gigabyte board with 4200 video and I am not seeing any problem....using drivers from the install.

---

### Post by Yahoé on 2014-01-24
After rtalcott comment I tried today's Xubuntu daily live but with the same problem. So I keep on using 3.12.0-7 for now. Since I have no idea what causes this issue I don't know against what I could open a bug report.

---

