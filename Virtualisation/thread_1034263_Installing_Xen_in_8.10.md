---
title: "Installing Xen in 8.10"
date: 2009-01-08
forum: Virtualisation
---

### Post by pontifikas on 2009-01-08
First of all, since this is my first post, I salute the Ubuntu community.

I want to install Xen and run some benchmarks as part of some homework for university.
I've tried everything, all Xen howto's for various distros, but to no avail.
Either the VM I create fails to start(I do this without rebooting in another kernel), or the Desktop manager fails to start when I boot the kernel created by xen-server.

I'm desperate and also dismayed since I believe I dont understand fundamental aspects of Xen, so I have a few questions on the procedure which may help me.

a) Do all kernels available in repositories, support Xen(even if hypervisor runs at domU, I dont care)??

b)By installing xen-server an image appears at /boot (xen-3.3.gz). Is this the kernel I have to boot on?? Is this kernel supporting all my devices? 
Cause I did use it and it did boot, but I ended in a black screen just before gnome started.

c)Some howtos refer to xen deamons while other dont. Why is that.

I thank you in advance
(Honestly, is there anyone how got Xen up and running in 8.10?)

---

### Post by bodhi.zazen on 2009-01-08
Xen dom0 (host) is not supported in 8.10, you need to use 8.04.

Xen domU (guest) is supported.

Xen seems to be falling out of favor and KVM is more popular. It seems even Fedora is not supporting Xen as much now as in the past.

If you search these forums there is another Xen thread here with comments.

---

