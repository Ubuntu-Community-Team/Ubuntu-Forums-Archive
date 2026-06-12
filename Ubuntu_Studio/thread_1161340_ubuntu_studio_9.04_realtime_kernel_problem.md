---
title: "ubuntu studio 9.04 realtime kernel problem"
date: 2009-05-16
forum: Ubuntu Studio
---

### Post by drbrook on 2009-05-16
Hi all,

Ubuntu 9.04 works fine for me, but as soon as I use the realtime kernel the system freezes after about 20 sec - 5 minutes. 
Any suggestions?

---

### Post by StudioDave on 2009-05-17
See the other threads in this forum that have to do with system freezes. I jumped through a series of hoops to get Jaunty/UStudio working, including a resolution of the mouse freeze problem. In my instance I added nosmp, acpi=off, and pnpbios=off to my kernel boot parameters (for the i386 version of US). That might work for you, or maybe not. Good luck, and be sure to read the other threads.

---

### Post by vivichrist on 2009-05-24
I went to [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D) and
grabed the 2.6.29-4 source deb and applied the rt16 patch to it from
[http://www.kernel.org/pub/linux/kernel/projects/rt/](http://www.kernel.org/pub/linux/kernel/projects/rt/). then copied across
the /boot/config-2.6.28-12-generic to that kernel source root directory.
did "make gconfig" and opened that config changed to full pre-emtion and
timing to 1000 like Luke Macneil has done. "make-kpkg clean" then
"CONCURRENCY_LEVEL=2 fakeroot make-kpkg --initrd --append-to-
version=-custom kernel_image kernel_headers" installed the resulting
packages headers first. and hey presto. note. CONCURRENCY_LEVEL=2
because my cpu is duel core and this required installation of certain
dev packages. this is amd64 though. can point you to a few sites if you need more details.

---

