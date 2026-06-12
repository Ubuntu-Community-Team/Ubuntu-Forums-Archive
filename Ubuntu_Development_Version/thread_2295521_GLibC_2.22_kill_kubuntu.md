---
title: "GLibC 2.22 kill kubuntu"
date: 2015-09-19
forum: Ubuntu Development Version
---

### Post by jffdtyd on 2015-09-19
after updating glibc my kubuntu died. xorg not start, someone else has this problem?

---

### Post by harry332 on 2015-09-19
Yes, the X was killed here too, with my Ubuntu.
I have tested it several times. Each time I upgrade glibc_2.21-0ubuntu4 into glibc_2.22-0ubuntu1, the X is killed.
I can only boot into tty1.

Downgrading glibc into v. 2.21 will not help, you will also need to reinstall xserver (packages xserver-common and xserver-xorg-core).
Then it is all good again.

---

### Post by harry332 on 2015-09-19
Here the original "bug".
[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1497473](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1497473)

So this is now blocked in proposed to solve the regressions.

---

