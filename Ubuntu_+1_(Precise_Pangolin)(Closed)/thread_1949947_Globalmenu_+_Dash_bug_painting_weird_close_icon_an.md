---
title: "Globalmenu + Dash bug: painting weird close icon and first letters"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sacridex on 2012-03-31
Hello,

on some devices the globalmenu has some errors with the most left thing to display, these errors also occur in the dash. I have attached some screenshots, the close button at maximized windows, the first letter in the globalmenu, and the first letter in the dash search and dash category description is painted wrong!
This problem does not occur on every device i've tested.

The painting is fine with a geforce 9600gt and the proprietary nvidia driver, it also works with a pentium su4100 and gma4500mhd.
But it is bugged with an Atom n270 or with a Radeon HD 4350 with proprietary driver.

---

### Post by coffeecat on 2012-03-31
This has been noticed before:

[http://ubuntuforums.org/showthread.php?t=1919448](http://ubuntuforums.org/showthread.php?t=1919448)

As you have found, it seems to occur only with some combinations of graphics-card/driver.

---

### Post by xREDEMPTIONx on 2012-03-31
This is a bug and a fix has been committed. Have a look here [https://bugs.launchpad.net/ubuntu/+source/nux/+bug/927441](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/927441)

---

