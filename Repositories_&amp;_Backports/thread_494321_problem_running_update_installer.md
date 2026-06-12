---
title: "problem running update installer"
date: 2007-07-06
forum: Repositories &amp; Backports
---

### Post by blightc on 2007-07-06
trying to run update installer and get 

E: /var/cache/apt/archives/libkrb53_1.4.4-5ubuntu3.1_i386.deb: files list file for package `evolution-webcal' is missing final newline

clearing the cache and retrying does no good
trying to uninstall evolution-webcal dies with the same error

now what ??

---

### Post by smartboyathome on 2007-07-06
Try installing it again. It may have been corrupt last time.

---

### Post by bapoumba on 2007-07-07
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189]("https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189")
Please check this bug report.

---

### Post by blightc on 2007-07-11
solution was here :

[https://answers.launchpad.net/ubuntu/+question/2591](https://answers.launchpad.net/ubuntu/+question/2591)

with the simple change of :

1) open terminal window
2) sudo su -
3) cd /var/lib/dpkg/info
4) cat -en '\n' >> ./evolution-webcal.list

retry the update installer and repeat for 2 more Evolution packages that had the same problem

---

