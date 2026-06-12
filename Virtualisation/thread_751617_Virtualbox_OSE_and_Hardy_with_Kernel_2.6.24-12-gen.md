---
title: "Virtualbox OSE and Hardy with Kernel 2.6.24-12-generic"
date: 2008-04-10
forum: Virtualisation
---

### Post by juanquivilla on 2008-04-10
Hey Guys,

I have the latest build of Hardy installed with all the updates. Due to a bug in kernel 2.6.24-15-generic, I am forced to use 2.6.24-12-generic until the bug fix is committed. Hardy provides the virtual box kernel modules ONLY for 2.6.24-15-[ARCH].

What is the proper way of downloading the source for the Virtual Box modules are recompiling with the kernel headers for 2.6.24-12-generic rather than 2.6.24-15-generic??

I would guess it's something like this:
apt-get source virtualbox-ose-modules-generic
cd into the folder
reconfigure with new kernel headers
etc...

Does this seem correct? Any pointers?

Thanks! :)

---

