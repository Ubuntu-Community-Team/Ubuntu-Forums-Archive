---
title: "Ubuntu 14.04 switchable graphics dpm not working correctly"
date: 2014-04-09
forum: Ubuntu Development Version
---

### Post by roudy1989 on 2014-04-09
Hi all,

I've opened a bug report for all those who are using AMD/Intel switchable graphics and got problems with the DPM support, too.
See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1304912](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/1304912).

The problem is that the radeon graphics card is shut down to dynoff but uses still a lot of power. The fan is spinning quite loud.
Mainline kernel 3.14 does not help so far.

Maybe we can solve this together quite fast :)

Cheers!

---

