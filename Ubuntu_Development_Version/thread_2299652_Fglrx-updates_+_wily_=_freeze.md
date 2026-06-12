---
title: "Fglrx-updates + wily = freeze"
date: 2015-10-20
forum: Ubuntu Development Version
---

### Post by nikolay-kuzmin on 2015-10-20
Is AMD proprietary driver from repo functional?
Installing either fglrx or fglrx-updates causes on my machine a freeze on bootup. 
Xorg's log doesn't show any errors, just ends on fglrx module loading. I can boot to root recovery console, "lsmod" shows fglrx loaded, "modprobe fglrx" doesn't exit until ctrl-c is pressed, "modprobe -vf fglrx" prints "exec format error".

---

### Post by howefield on 2015-10-20
> **nikolay-kuzmin said:**
> Is AMD proprietary driver from repo functional?

I'd say not, having the same (or similar) issue for about a week.

Just about to zsync todays image and try again.

---

### Post by cariboo on 2015-10-20
My Intel based system was freezing yup for a couple of  weeks, but updates seem to have solved the problem.

---

### Post by P-I H on 2015-10-20
According to Phoronix the Catalyst driver will not work. There are also problems with some Radeon cards. However my Radeon R9 380 works fine with AMDGPU.
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-4.2-Cat-Not-Ready](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-4.2-Cat-Not-Ready)

---

