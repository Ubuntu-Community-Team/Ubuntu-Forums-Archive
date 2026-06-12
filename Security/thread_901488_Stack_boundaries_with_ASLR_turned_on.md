---
title: "Stack boundaries with ASLR turned on"
date: 2008-08-26
forum: Security
---

### Post by ClarkC on 2008-08-26
I am working on a security research project (intelligence agencies grant). We run executables in a virtual machine environment (specifically, using SDT -- Software Dynamic Translation) to protect them at run time. One of the protection mechanisms shadows the stack addresses.

When porting to an Ubuntu distribution, we have encountered a problem due to ASR a.k.a. ASLR (Address Space [Layout] Randomization). We formerly computed the bounds on the stack we were shadowing as follows:

  getrlimit(RLIMIT_STACK, &rlim);
  top_of_stack = bottom_of_stack - rlim.rlim_cur;

We had used a constant value for bottom_of_stack that worked on our original Linux distribution, namely 0xbffff000. However, the ASLR on Ubuntu works differently than on the other Linux distribution and this value for the bottom of the stack is invalid.

How can we obtain the real bottom of the stack at run time when ASLR is turned on?

Thanks for any pointers.

uname -rv output:
2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008

---

### Post by ClarkC on 2008-08-29
Bumping this. Does anyone think this would be better asked in a forum other than Security? If so, which one? Thanks.

---

