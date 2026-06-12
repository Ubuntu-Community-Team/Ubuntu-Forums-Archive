---
title: "No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'"
date: 2010-08-04
forum: Ubuntu Studio
---

### Post by skmprabhu on 2010-08-04
Hi all,

I am new to kernel programming and the linux. i tried to run hello module yesterday but i am getting below error. please help me to solve this error.

prabhu@MSYS-ENG-0102:/usr/src/linux-source-2.6.31/demo$ sudo make
make -C /lib/modules/2.6.31-14-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2



My hello.c file:
#include <linux/module.h>       /* Needed by all modules */
#include <linux/kernel.h>       /* Needed for KERN_INFO */
#include <linux/init.h>         /* Needed for the macros */

static int __init hello_start(void)
{
printk(KERN_INFO "Loading hello module...\n");
printk(KERN_INFO "Hello world\n");
return 0;
}

static void __exit hello_end(void)
{
printk(KERN_INFO "Goodbye Mr.\n");
}

module_init(hello_start);
module_exit(hello_end);

my Makefile is 

obj-m += hello.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean



---------------------------------------
please suggest me best guide(or book) for kernel programming....

---

### Post by gloria0227 on 2010-08-26
I am also getting a No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. error, any ideas anyone?

---

