---
title: "VMWare Server 2.0.0 on 2.6.24-21-server kernel"
date: 2008-10-19
forum: Virtualisation
---

### Post by herald on 2008-10-19
OK so I've recently upgraded to the 2.6.24-21-server kernel and of course vmware server stops working.  I installed the kernel-headers for the new kernel.  I dutifully download the latest any-any update (117d from vmware kernel newbies on google groups) and run it.  It seems to take just fine, but then when running the vmware-config.pl script, I get a compile error on bridge.c, in the vmnet-only section.  I seem to remember there was something one had to do to get past this, like a patch to vmware-any-any or something, but I can't remember.  Anyone know?  Thanks!
-Herald

---

### Post by bodhi.zazen on 2008-10-19
I would not use the any-any patch ;)

It patches the code and is (was ) not needed last time I updated.

I suggest you download a new copy of VMWare and try installing following the sticky without using teh any-any patch.

---

### Post by herald on 2008-10-19
Yep, you're absolutely right.  I fell pray to the oldest rule in the book: Don't make more than one change without testing first.

To make a long story short, I didn't have the new kernel-header libraries installed before running vmware-config.pl.  That made me jump to the any-any update, which, as Ubuntu works without it, gave me yet more errors.

The instructions in the Vmware Howto work just fine, and I fail as a troubleshooter.  Thanks for the help!

---

### Post by bodhi.zazen on 2008-10-19
Thanks for the feedback, it helps me to help others as well ;)

---

