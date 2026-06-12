---
title: "linux kernel"
date: 2006-06-16
forum: The Cafe
---

### Post by thero on 2006-06-16
I notice in the repositories and kernel.org that there are two versions of the Linux kernel.  2.4 and 2.6.  What's the difference between the two?

---

### Post by iball on 2006-06-16
2.6 is the latest series, 2.4 was the previous one.

Many servers still run a 2.4 kernel, because of its proven track record of stability.  It is still maintained, with security patches and such, but it is not actively maintained.  Slackware Linux and Debian Sarge still uses a 2.4 kernel by default.

2.6 is the current series.  It is used by default on most current distros, including Ubuntu.  It is fine for desktops, and stable enough now for servers.  It is faster than 2.4, and has more features.

--Ian

---

### Post by jdong on 2006-06-16
There are also some other reasons for 2.4 being actively maintained:

* there are still servers that are just fine with 2.4 and see no point in upgrading. Upgrading to the 2.6 kernel is a pretty invasive operation, and in some environments it's simply not practical.

* Embedded devices seem to use 2.4 a lot more than 2.6. The toolchain/support around 2.4 is somewhat more mature/documented than 2.6.

* 2.4 is a traditional definition of a stable kernel: bugfix only, no new features. Since it's been around for SO long, that means virtually every bug has been squashed (ok, maybe that's stretching it). Meanwhile, 2.6 introduces new features every release that make us desktop users happy but server administrators uneasy.

* 2.4 supports some types of hardware better than 2.6, including the weird IDE/ATA motherboard RAID controllers.


Finally, the bottom line is, there is still interest in maintaining the 2.4 kernel tree. And, by the open source spirit, as long as there is interest, a product will not be abandoned just because the creator (Linus) has moved on to bigger and newer things (2.6).

---

