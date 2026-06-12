---
title: "Arch Linux doesn't boot in virtualbox"
date: 2013-12-26
forum: Virtualisation
---

### Post by adityashah30 on 2013-12-26
Hi guys,
I have been meaning to install arch linux in my virtualbox so as to learn and tinker around. But the problem is that when i start the virtual machine, after the splash screen nothing else shows. It just defaults to a blank screen and it stays there only. T have tested the iso image that i have by successfully booting it in vmware on windows. But, since most of my work is done in linux, i would prefer if  I could install it in virtualbox on ubuntu.
I use ubuntu 12.04.3 lts with 3.8.0-34-generic kernel from the raring hwe stack.
Thanks

---

### Post by hoopia on 2013-12-28
Go to the VM's settings->Display. On the Video tab, uncheck Enable 3D Acceleration. I've seen this once before and remember this being a solution.

---

### Post by adityashah30 on 2013-12-29
Even with 3D acceleration disabled, the problem still persists!

---

### Post by jdeca57 on 2014-01-04
I had the same problem and I believe it's related to the version of Virtualbox used in 12.04. If you use a more recent version (I manually installed VB 4.3.6 under OpenSUSE 13.1) then Arch works. The problem is that kernels move on and the versions of VB remain the same on LTS. Debian has similar problems. And of course, overriding it like I did on the test system with OpenSUSE negates the whole point of LTS: stability.

---

### Post by adityashah30 on 2014-01-09
Thanks! Installing the latest version from oracle website solved the problem! But yes, I agree with you. This negates the whole point of stability!

---

