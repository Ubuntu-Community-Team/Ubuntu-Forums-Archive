---
title: "Warnings on compiling 2.6 kernel for xen"
date: 2009-12-16
forum: Virtualisation
---

### Post by kai.scorpio on 2009-12-16
I'm completely new to this kind of work, so I'd just like to check if what's going on is a serious problem. This is built from development source, so I expect minor errors simply haven't been fixed yet.
I'm following the instructions here: [http://www.itkovian.net/base/xen_hypervisor_with_ubuntu_karmic_koala](http://www.itkovian.net/base/xen_hypervisor_with_ubuntu_karmic_koala)

When I get to the stage of compiling my kernel, I get several warnings, mostly that "xxx exceeds the page size of 1024" and 15 section mismatches. However, it continues to compile, so I'd just like to know if this is normal/serious?

The kernel is still compiling when I posted this, so I'll update this when I try to run it.

---

### Post by kai.scorpio on 2009-12-17
I've run into a problem when I try to boot it, I get an error:
'gave up waiting for root device'
and then get the (initramfs) shell. I don't know if this has anything to do with my compiling errors, so this may or may not be solved.

---

