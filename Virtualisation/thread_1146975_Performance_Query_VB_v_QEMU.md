---
title: "Performance Query: VB v QEMU"
date: 2009-05-03
forum: Virtualisation
---

### Post by GuiGuy on 2009-05-03
I've installed the licensed Sun VirtualBox on my jaunty desktop PC. No sooner done and I read that all other things being equal, VirtualBox under performs by a factor of half compared to qemu. 

Comments?

---

### Post by bodhi.zazen on 2009-05-03
First, the teminology is a bit confusing.

qemu = [http://www.nongnu.org/qemu/download.html](http://www.nongnu.org/qemu/download.html)

On the same page you can see information of kqemu ( "QEMU Accelerator Module ")

kvm is hardware acceleration and is built on qemu : [http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)

Virtualbox is built on qemu / kvm, and to support 64 bit guests you need to have a cpu that  supports KVM.

virtualbox is faster then qemu, even with kqemu (qemu acceleration module).

If you hardware supports KVM , virtualbox is a tad slower then KVM, IMO, but not by much.

---

### Post by GuiGuy on 2009-05-03
> **bodhi.zazen said:**
> 
virtualbox is faster then qemu, even with kqemu (qemu acceleration module).
If you hardware supports KVM , virtualbox is a tad slower then KVM, IMO, but not by much.

Thanks for that. That is my situation so it looks like I fluked the correct choice. 

Cheers

---

