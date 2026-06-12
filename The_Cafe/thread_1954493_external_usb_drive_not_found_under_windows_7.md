---
title: "external usb drive not found under windows 7"
date: 2012-04-08
forum: The Cafe
---

### Post by jbenowl16 on 2012-04-08
Ubuntu chose to install on an external USB Drive that I partitioned according to recommendation. I have gone back to windows boot screen and now cannot find the Ubuntu drive. How can I find it again?

---

### Post by howefield on 2012-04-08
If you have formatted your external disk to an ext file system Windows won't be able to see it it without a third party application. (not sure how stable those are)

---

### Post by 3rdalbum on 2012-04-08
The Windows boot screen will not see your Ubuntu drive; the Windows boot screen only boots Windows.

You will need to change your BIOS settings so it looks for the USB drive first, and if it doesn't find it THEN it looks on your hard disk and boots Windows.

Currently it seems that your BIOS is looking at the hard disk before it looks at the USB. It should be fairly trivial to change the boot order to prioritise the USB.

---

### Post by jbenowl16 on 2012-04-08
I have found the perfect solution now, thanks! I downloaded Easy BCD and set it up. Problem solved! Windows 7 and Ubuntu now both appear on the boot menu enabling me to choose which I want to use.
Simples!

---

