---
title: "why does linking simple cpp example for ulockmgr_op() for fuse filesystem fail?"
date: 2016-02-24
forum: Ubuntu Application Development
---

### Post by thinking on 2016-02-24
Hi all,

i'm working on a fuse filesystem where i try to implement the lock() function
which in the standard example uses ulockmgr_op().
(The example can be found here: [http://web.mit.edu/~ecprice/fuse-2.7.0/example/fusexmp_fh.c](http://web.mit.edu/~ecprice/fuse-2.7.0/example/fusexmp_fh.c) in function xmp_lock)

My dev-setup:
OS: ubuntu 14.04.4 lts
header: ulockmgr_op is defined in /usr/include/ulockmgr.h as int ulockmgr_op(int fd, int cmd, struct flock *lock, const void *owner, size_t owner_len);
library: the shared object is in /lib/x86_64-linux-gnu/libulockmgr.so.1.0.1 and a symlink libulockmgr.so.1
linker path: contains /lib/x86_64-linux-gnu

the library is installed by libfuse2 package

the example:
```

#include <ulockmgr.h>
#include <iostream>

int main(int argc, char **argv){
    std::cout << ulockmgr_op(0, 0, NULL, NULL, 0) << std::endl;
    return 0;
}

```

compiling works:
g++ -c -o ulockmgr.o ulockmgr.cpp

linking fails:
user@user-desktop:~/data$ g++ -o ulockmgr -lulockmgr ulockmgr.cpp
/tmp/ccNSGocY.o: In function `main':
ulockmgr.cpp:(.text+0x2a): undefined reference to `ulockmgr_op(int, int, flock*, void const*, unsigned long)'
collect2: error: ld returned 1 exit status

what i tried:
[LIST]
[*] changing -lulockmgr to -lulockmgr1 which results in the error /usr/bin/ld: cannot find -lulockmgr1
    this means, the ulockmgr library is truly found!
[*] using "nm -D libulockmgr.so.1" shows that the function is really defined: "0000000000001070 T ulockmgr_op"
[*] i also tried to link using
    g++ -lulockmgr -o ulockmgr -lulockmgr ulockmgr.cpp -lulockmgr
    in case the library ordering for the linker was wrong - i get the same error
[/LIST]

So my question: can anybody get my simple example to link successfully? Anybody knows what might be wrong with my setup/example?
Btw: i'm not interested in really running this example - i just need to get it to link at least

---

### Post by steeldriver on 2016-02-24
I suspect it's something to do with name mangling - as a result of trying to use a C header in C++ 

You would probably find that a C equivalent

```

#include <ulockmgr.h>
#include <stdio.h>

int main(int argc, char **argv){
    printf("%d\n", ulockmgr_op(0, 0, NULL, NULL, 0));
    return 0;
}

```

compiles & links happily with gcc

```

gcc -o ulockmgr ulockmgr.c -lulockmgr

```

---

### Post by thinking on 2016-02-25
yeah - you're right - thank you very much

the following c++ code links without problems
```

extern "C"{
#include <ulockmgr.h>
}
#include <iostream>

int main(int argc, char **argv){
    std::cout << ulockmgr_op(0, 0, NULL, NULL, 0) << std::endl;
    return 0;
}

```

---

