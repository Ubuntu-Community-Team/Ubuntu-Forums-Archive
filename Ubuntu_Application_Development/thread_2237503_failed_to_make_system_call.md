---
title: "failed to make system call"
date: 2014-08-02
forum: Ubuntu Application Development
---

### Post by zerop2 on 2014-08-02
[http://people.ee.ethz.ch/~arkeller/linux/kernel_user_space_howto.html#ss5.2](http://people.ee.ethz.ch/~arkeller/linux/kernel_user_space_howto.html#ss5.2)


firstly can not find
arch/i386/kernel/syscall_table.S
This file is a table with all the available system calls. In order to make your call accessible add the following line at the bottom of this file:
         .long sys_mycall


then, do not know which directory added to this option


core-y = ????


Add the new directory to the variable core-y (search for core-y.*+=) in the top level Makefile




after compile module and insmod and then compile
the user space program and run


no printf message in dmesg

---

