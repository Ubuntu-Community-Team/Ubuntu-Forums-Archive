---
title: "Kernel Command Line and Debian Installer Environment"
date: 2017-12-05
forum: Ubuntu Development Version
---

### Post by steffel2 on 2017-12-05
Hi,

I'm setting up a new customized installer image (before 14.04, now 18.04). 

Did anything change with command line parsing in 18.04 installer environment? In 14.04 I could preseed some variables by linux command line (e.g. keyboard-configuration/modelcode=SKIP), but in 18.04 installer environment, it seems that parameters with dashes or slashes are not taken into environment.
/proc/cmdline still shows the parameters, but env doesn't. And then, env2debconf can't bring the variables into debconf database.

In 14.04 environment, those variables were put into environment.
Taking busybox 1.21.0 from 14.04 and put into 18.04 initrd (replacing busybox 1.27.2) - and the environment has those variables, again.

I already compared busybox sources, but didn't find a certain clue.

Has anyone a hint for me? Thanks a lot!

---

### Post by dino99 on 2017-12-05
you should have better asked on askubuntu, to get a more complete answer from devs
[https://askubuntu.com/](https://askubuntu.com/)

---

### Post by steffel2 on 2017-12-05
After hours of analysing (and patching busybox) I found the root of the problem in busybox.
A fix was already committed, but not released. Ubuntu has to integrate the next version of busybox.

[https://git.busybox.net/busybox/commit/shell/ash.c?id=9c143ce52da11ec3d21a3491c3749841d3dc10f0](https://git.busybox.net/busybox/commit/shell/ash.c?id=9c143ce52da11ec3d21a3491c3749841d3dc10f0)

I created an issue on launchpad: [https://bugs.launchpad.net/ubuntu/+source/busybox/+bug/1736421](https://bugs.launchpad.net/ubuntu/+source/busybox/+bug/1736421)

---

