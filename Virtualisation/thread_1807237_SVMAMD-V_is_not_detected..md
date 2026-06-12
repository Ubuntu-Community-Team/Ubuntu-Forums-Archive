---
title: "SVM/AMD-V is not detected."
date: 2011-07-18
forum: Virtualisation
---

### Post by shadowsall on 2011-07-18
I am running a xen image I grabbed from the repository(2.6.32-5-xen-amd64). I have a AMD Opteron 6128 that indeed has SVM/AMD-V capabilities and the BIOS has SVM enabled. When I query /proc/cpuinfo with "grep svm /proc/cpuinfo," grep returns nothing. I have booted Fedora, Ubuntu, and Gentoo Live CDs and both see the SVM extensions for my CPU. Why is Debian/Xen unable to see the SVM extension? I need HVM capabilities to run Windows guests.

EDIT: I'm running Debian Squeeze and Xen 4.0.1

---

