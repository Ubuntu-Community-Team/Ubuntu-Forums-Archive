---
title: "Frequent Load Cycles"
date: 2007-11-02
forum: System76 Support
---

### Post by Skia_42 on 2007-11-02
I recently came across this [bug.]("https://launchpad.net/bug59695.html") Apparently the current power configuration leads to frequent load cycles. I purchased a gazv4 System76 laptop sometime in May and have already gone through 265653 load cycles. Most laptop drives handle around 600000 load cycles before things start to break.

Does System76 know about this? I wanted to check, I think that this is an important issue that should be fixed.

---

### Post by thomasaaron on 2007-11-02
Did you try the fix mentioned in that bug report?
And if so, did it work?

---

### Post by Skia_42 on 2007-11-02
I was able to fix the problem with this:> 
1) make a file named "99-hdd-spin-fix.sh". The important thing is starting with "99".
2) make sure the file contains the following 2 lines (fix it if you have PATA HDD):
#!/bin/sh
hdparm -B 255 /dev/sda
3) copy this file to 3 locations:
/etc/acpi/suspend.d/
/etc/acpi/resume.d/
/etc/acpi/start.d/

It looks like the problem is fixed, I'll check back in a few days. Hope that helps.

---

### Post by vivedekananda on 2007-11-04
If you use windows, check if you don't have similar problem there and if you have it (like I did) you can fix it with windows version of hdparm.

---

