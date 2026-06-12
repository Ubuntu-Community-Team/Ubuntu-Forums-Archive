---
title: "gmon.out: No such file or directory"
date: 2014-07-27
forum: Ubuntu Application Development
---

### Post by zerop2 on 2014-07-27
wonder@wonder-VirtualBox:~/layer$ ls
built-in.o  gprof.output  hello.mod.c  main.c     modules.order   tempfile
cli.c       hello.c       hello.mod.o  main.c~    Module.symvers
cli.c~      hello.c~      hello.o      Makefile   snull.h
core        hello.ko      main         Makefile~  sysdep.h
wonder@wonder-VirtualBox:~/layer$ sudo gprof ./hello.ogmon.out: No such file or directory

```

ccflags-y += -pg # enable profiling
obj-m += hello.o

hello.o:
    make -o hello -C /usr/src/linux-headers-3.8.0-29-generic -C /usr/include/i386-linux-gnu/sys M=$(PWD) modules

clean:
    make -C /usr/src/linux-headers-3.8.0-29-generic -C /usr/include/i386-linux-gnu/sys M=$(PWD) clean

```

---

