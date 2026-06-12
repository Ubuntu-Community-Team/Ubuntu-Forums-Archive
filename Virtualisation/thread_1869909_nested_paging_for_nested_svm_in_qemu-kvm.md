---
title: "nested paging for nested svm in qemu-kvm"
date: 2011-10-26
forum: Virtualisation
---

### Post by Deepak Goel on 2011-10-26
Hi,

I am facing issues while trying nested virtualization (kvm over kvm).
 
Here is my environment details:

Machine - Quad-Core AMD Opteron(tm) Processor 1389 (64bits)
Host OS - ubuntu 11.10 (32bits)
Linux kernel - 3.0.7

First level Guest
OS - ubuntu 10.10 (32bits)

Second level Guest
OS - ubuntu 10.10 (32bits)

qemu-kvm version - 14

Command line to start the guest
qemu-kvm -m 1024 -cpu phenom -enable-nesting -hda ubuntu11.img

I could get nested svm support but not nested npt support in my first level guest. Also, I saw that the first level guest is not exposing npt flag in /proc/cpuinfo

Am I missing something here? I appreciate any help towards resolving this issue.

Thanks in Advance.

---

