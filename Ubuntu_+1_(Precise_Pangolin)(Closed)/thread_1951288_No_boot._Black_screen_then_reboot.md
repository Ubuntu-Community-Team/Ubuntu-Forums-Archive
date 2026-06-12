---
title: "No boot. Black screen then reboot"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by foxmulder881 on 2012-04-02
This is really starting to p*** me off. What the hell is the difference between the 3.0 and 3.2 kernel? It's obviously something quite important. I can not get Ubuntu 12.04 or Fedora 16 to boot. And I can only put it down to being something to do with the kernel used in 12.04.

In both Ubuntu and Fedora, I get the boot menu. But when I select to boot the screen goes black and then the system reboots. And the same thing happens in VirtualBox also.

Any Linux OS running kernel 3.0 and under works fine. It seems anything with kernel 3.2 does not work. Early version of 12.04 were working fine.

Any help and advice would be handy.

---

### Post by foxmulder881 on 2012-04-05
Sadly, I've had no progress. I've just about given up on mainstream distros. :-(

---

### Post by dino99 on 2012-04-05
depending of your hardware maybe you need to try booting with some options

see "kernel boot options" scrolling down

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

then your logs might help you know whats about that issue

---

### Post by ronacc on 2012-04-05
are you trying to boot the livecd or an installation ? if an installation is it a fresh install or an upgraded install ? if an install try removing quiet splash from the bootline and see what happens just before it reboots .

---

### Post by ronacc on 2012-04-05
also if it is an older box you might want to see kansasnoob's thread about non-pae kernels [ http://ubuntuforums.org/showthread.php?t=1924455&highlight=pae ]( http://ubuntuforums.org/showthread.php?t=1924455&highlight=pae )

---

