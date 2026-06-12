---
title: "Ubuntu 10.4 - Qemulater / winxp vm slow"
date: 2010-10-01
forum: Virtualisation
---

### Post by kryg3r on 2010-10-01
noob here, very frighten still for all the -commands, so instead of dedicating a day or 5 to figure out how to install a novell client module (cannot seem to get wine to work), i thought since qemulater is installed, i might as well install a winxp vm with NAT setting. at least then i can do my office work. settled with 1gb memory and it took the installation 1hour.
i dont have a slow notebook, and my settings is set for alot of memory, but why is everything so slow on the vm? did i do anything wrong? my allocated hdd space is at least 10gb. when i move the cursor its fast, but when i click on anything its relatively "go have some tea in the meanwhile" slow.
i use ubuntu ultimate 2.7, a intel duo 1.8 with 2gb ram
is it 1. the qemu that is acting silly, 2. my hardware, 3 ubuntu's way of telling me there is other ways of getting my novell to work?

----
Computer science is no more about computers than  astronomy is about telescopes.

---

### Post by gordintoronto on 2010-10-01
Just a thought:

"KVM requires your system to support hardware virtualization, provided by AMD's SVM capability or Intel's VT. To find out if your processor has the necessary support:

  egrep "flags.*:.*(svm|vmx)" /proc/cpuinfo"

Most Ubuntu users who try virtualization use Virtualbox, so it might be difficult to get help with Qemu-kvm.

---

### Post by kryg3r on 2010-10-01
thank you. it didnt support it.

---

