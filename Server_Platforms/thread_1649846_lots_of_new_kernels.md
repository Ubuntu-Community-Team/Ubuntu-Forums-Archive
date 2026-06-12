---
title: "lots of new kernels"
date: 2010-12-20
forum: Server Platforms
---

### Post by Vegan on 2010-12-20
I see that since I installed 10.10 there have been several new kernel releases on the updates

guess the kernel maintainers are fixing defects faster of late

now if only they would allow **powertop** to work better

can somebody make a shell script to enable

CONFIG_PM_ADVANCED_DEBUG

---

### Post by stmiller on 2010-12-20
(Ubuntu never updates a kernel version in a release.) What you are seeing are security patches to the same kernel. 

([http://www.ubuntu.com/usn](http://www.ubuntu.com/usn))

Changing something like this:

CONFIG_PM_ADVANCED_DEBUG

is only available via configuring and recompiling your own kernel. :) Unless you are debugging some power management code, I wouldn't bother. :P

---

