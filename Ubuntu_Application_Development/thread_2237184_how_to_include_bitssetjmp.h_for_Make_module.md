---
title: "how to include bits/setjmp.h for Make module"
date: 2014-07-31
forum: Ubuntu Application Development
---

### Post by zerop2 on 2014-07-31
i already comment the never include bits/setjmp.h

tried many command to make module, how to make for the file include <bits/setjmp.h> 
for try and catch exception in module

wonder@wonder-VirtualBox:~/layer$ sudo make -C /usr/src/linux-headers-3.8.0-29-generic hello.c M=/home/wonder/layer modules
make: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
make: Nothing to be done for `/home/wonder/layer/hello.c'.
  CC [M]  /home/wonder/layer/hello.o
/home/wonder/layer/hello.c:10:25: fatal error: bits/setjmp.h: No such file or directory
compilation terminated.
make[1]: *** [/home/wonder/layer/hello.o] Error 1
make: *** [_module_/home/wonder/layer] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'
wonder@wonder-VirtualBox:~/layer$ sudo make -C /usr/src/linux-headers-3.8.0-29-generic -C /usr/include/i386-linux-gnu/sys -C /usr/include/i386-linux-gnu hello.c M=/home/wonder/layer modules
make: Entering directory `/usr/include/i386-linux-gnu'
make: *** No rule to make target `hello.c'.  Stop.
make: Leaving directory `/usr/include/i386-linux-gnu'
wonder@wonder-VirtualBox:~/layer$ 



Makefile
```

ccflags-y += -pg # enable profiling
obj-m += hello.o

hello.o:
    make -o hello -C /usr/src/linux-headers-3.8.0-29-generic -C /usr/include/i386-linux-gnu/sys -C /usr/include/i386-linux-gnu M=$(PWD) modules

clean:
    make -C /usr/src/linux-headers-3.8.0-29-generic -C /usr/include/i386-linux-gnu/sys M=$(PWD) clean

```

---

### Post by TheFu on 2014-07-31
Pass the **-I /path/to/directory** into the compiler. **man cc** will explain.  Also, having a makefile call make is really odd and tying to "make" anything inside an include directory doesn't make sense to me. Perhaps there is something strange happening, but I've never seen that in all my years.

I would try to explain more, but I don't know where to start with the existing example above. Just haven't seen anything like that before.  My base Makefile it too long to post here, tabs would be lost, and doesn't use the modern methods for automatic dependency insertion. Sorry.  
Found [this site]("http://www.cs.swarthmore.edu/~newhall/unixhelp/howto_makefiles.html#C") with examples that may be helpful.

---

