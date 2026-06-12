---
title: "totally new, need help"
date: 2005-09-27
forum: Repositories &amp; Backports
---

### Post by allamericanjeep on 2005-09-27
so i was going through the ubuntu guide and am trying to install the java runtime enviroment. when i try to the terminal says. . .
"W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5
"
i thought there was a typo in my list, but i copied and pasted like 4 times. is there something im donig wrong?
thank you
Chris

---

### Post by aysiu on 2005-09-27
Have you tried commenting out the CD-ROM source?
Just stick a # sign in front of that line.

---

### Post by John.Michael.Kane on 2005-09-28
sun-j2re1.5=removed from repo's. so it's not avilable..

---

