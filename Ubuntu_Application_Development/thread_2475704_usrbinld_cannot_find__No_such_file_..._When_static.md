---
title: "/usr/bin/ld: cannot find : No such file ... When static compiling"
date: 2022-06-05
forum: Ubuntu Application Development
---

### Post by perlish on 2022-06-05
I static compile this code [https://github.com/kris-nova/boopkit.git](https://github.com/kris-nova/boopkit.git) ,it shows some error like below:


```
k8s@k8s:~/boopkit$ make static
-> Building boopkit
gcc -I/usr/local/include -g -lbpf -lelf -lpcap -lpthread -static -o boopkit boopkit.c common.c dpi.c -Wl,
/usr/bin/ld: cannot find : No such file or directory
collect2: error: ld returned 1 exit status
make: *** [Makefile:71: static] Error 1
```


And I add -v to find the detail:
```
k8s@k8s:~/boopkit$ gcc -I/usr/local/include -g -lbpf -lelf -lpcap -lpthread -static -o boopkit boopkit.c common.c dpi.c -Wl, -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/11/lto-wrapper
OFFLOAD_TARGET_NAMES=nvptx-none:amdgcn-amdhsa
OFFLOAD_TARGET_DEFAULT=1
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 11.3.0-3ubuntu1' --with-bugurl=file:///usr/share/doc/gcc-11/README.Bugs --enable-languages=c,ada,c++,go,brig,d,fortran,objc,obj-c++,m2 --prefix=/usr --with-gcc-major-version-only --program-suffix=-11 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --enable-bootstrap --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --enable-default-pie --with-system-zlib --enable-libphobos-checking=release --with-target-system-zlib=auto --enable-objc-gc=auto --enable-multiarch --disable-werror --enable-cet --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-offload-targets=nvptx-none=/build/gcc-11-pWJoHK/gcc-11-11.3.0/debian/tmp-nvptx/usr,amdgcn-amdhsa=/build/gcc-11-pWJoHK/gcc-11-11.3.0/debian/tmp-gcn/usr --without-cuda-driver --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu --with-build-config=bootstrap-lto-lean --enable-link-serialization=2
Thread model: posix
Supported LTO compression algorithms: zlib zstd
gcc version 11.3.0 (Ubuntu 11.3.0-3ubuntu1)
COLLECT_GCC_OPTIONS='-I' '/usr/local/include' '-g' '-static' '-o' 'boopkit' '-v' '-mtune=generic' '-march=x86-64' '-dumpdir' 'boopkit-'
/usr/lib/gcc/x86_64-linux-gnu/11/cc1 -quiet -v -I /usr/local/include -imultiarch x86_64-linux-gnu boopkit.c -quiet -dumpdir boopkit- -dumpbase boopkit.c -dumpbase-ext .c -mtune=generic -march=x86-64 -g -version -fasynchronous-unwind-tables -fstack-protector-strong -Wformat -Wformat-security -fstack-clash-protection -fcf-protection -o /tmp/ccOtr1mS.s
GNU C17 (Ubuntu 11.3.0-3ubuntu1) version 11.3.0 (x86_64-linux-gnu)
compiled by GNU C version 11.3.0, GMP version 6.2.1, MPFR version 4.1.0, MPC version 1.2.1, isl version isl-0.24-GMP


GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/11/include-fixed"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/11/../../../../x86_64-linux-gnu/include"
ignoring duplicate directory "/usr/local/include"
as it is a non-system directory that duplicates a system directory
#include "..." search starts here:
#include <...> search starts here:
/usr/lib/gcc/x86_64-linux-gnu/11/include
/usr/local/include
/usr/include/x86_64-linux-gnu
/usr/include
End of search list.
GNU C17 (Ubuntu 11.3.0-3ubuntu1) version 11.3.0 (x86_64-linux-gnu)
compiled by GNU C version 11.3.0, GMP version 6.2.1, MPFR version 4.1.0, MPC version 1.2.1, isl version isl-0.24-GMP


GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: e9f3cebf5e5d804b6e7b4929615d6e26
COLLECT_GCC_OPTIONS='-I' '/usr/local/include' '-g' '-static' '-o' 'boopkit' '-v' '-mtune=generic' '-march=x86-64' '-dumpdir' 'boopkit-'
as -v -I /usr/local/include --gdwarf-5 --64 -o /tmp/ccJQGe9q.o /tmp/ccOtr1mS.s
GNU assembler version 2.38 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.38
COLLECT_GCC_OPTIONS='-I' '/usr/local/include' '-g' '-static' '-o' 'boopkit' '-v' '-mtune=generic' '-march=x86-64' '-dumpdir' 'boopkit-'
/usr/lib/gcc/x86_64-linux-gnu/11/cc1 -quiet -v -I /usr/local/include -imultiarch x86_64-linux-gnu common.c -quiet -dumpdir boopkit- -dumpbase common.c -dumpbase-ext .c -mtune=generic -march=x86-64 -g -version -fasynchronous-unwind-tables -fstack-protector-strong -Wformat -Wformat-security -fstack-clash-protection -fcf-protection -o /tmp/ccOtr1mS.s
GNU C17 (Ubuntu 11.3.0-3ubuntu1) version 11.3.0 (x86_64-linux-gnu)
compiled by GNU C version 11.3.0, GMP version 6.2.1, MPFR version 4.1.0, MPC version 1.2.1, isl version isl-0.24-GMP


GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/11/include-fixed"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/11/../../../../x86_64-linux-gnu/include"
ignoring duplicate directory "/usr/local/include"
as it is a non-system directory that duplicates a system directory
#include "..." search starts here:
#include <...> search starts here:
/usr/lib/gcc/x86_64-linux-gnu/11/include
/usr/local/include
/usr/include/x86_64-linux-gnu
/usr/include
End of search list.
GNU C17 (Ubuntu 11.3.0-3ubuntu1) version 11.3.0 (x86_64-linux-gnu)
compiled by GNU C version 11.3.0, GMP version 6.2.1, MPFR version 4.1.0, MPC version 1.2.1, isl version isl-0.24-GMP


GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: e9f3cebf5e5d804b6e7b4929615d6e26
COLLECT_GCC_OPTIONS='-I' '/usr/local/include' '-g' '-static' '-o' 'boopkit' '-v' '-mtune=generic' '-march=x86-64' '-dumpdir' 'boopkit-'
as -v -I /usr/local/include --gdwarf-5 --64 -o /tmp/ccmNmmR6.o /tmp/ccOtr1mS.s
GNU assembler version 2.38 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.38
COLLECT_GCC_OPTIONS='-I' '/usr/local/include' '-g' '-static' '-o' 'boopkit' '-v' '-mtune=generic' '-march=x86-64' '-dumpdir' 'boopkit-'
/usr/lib/gcc/x86_64-linux-gnu/11/cc1 -quiet -v -I /usr/local/include -imultiarch x86_64-linux-gnu dpi.c -quiet -dumpdir boopkit- -dumpbase dpi.c -dumpbase-ext .c -mtune=generic -march=x86-64 -g -version -fasynchronous-unwind-tables -fstack-protector-strong -Wformat -Wformat-security -fstack-clash-protection -fcf-protection -o /tmp/ccOtr1mS.s
GNU C17 (Ubuntu 11.3.0-3ubuntu1) version 11.3.0 (x86_64-linux-gnu)
compiled by GNU C version 11.3.0, GMP version 6.2.1, MPFR version 4.1.0, MPC version 1.2.1, isl version isl-0.24-GMP


GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/11/include-fixed"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/11/../../../../x86_64-linux-gnu/include"
ignoring duplicate directory "/usr/local/include"
as it is a non-system directory that duplicates a system directory
#include "..." search starts here:
#include <...> search starts here:
/usr/lib/gcc/x86_64-linux-gnu/11/include
/usr/local/include
/usr/include/x86_64-linux-gnu
/usr/include
End of search list.
GNU C17 (Ubuntu 11.3.0-3ubuntu1) version 11.3.0 (x86_64-linux-gnu)
compiled by GNU C version 11.3.0, GMP version 6.2.1, MPFR version 4.1.0, MPC version 1.2.1, isl version isl-0.24-GMP


GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: e9f3cebf5e5d804b6e7b4929615d6e26
COLLECT_GCC_OPTIONS='-I' '/usr/local/include' '-g' '-static' '-o' 'boopkit' '-v' '-mtune=generic' '-march=x86-64' '-dumpdir' 'boopkit-'
as -v -I /usr/local/include --gdwarf-5 --64 -o /tmp/cct0qgmh.o /tmp/ccOtr1mS.s
GNU assembler version 2.38 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.38
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/11/:/usr/lib/gcc/x86_64-linux-gnu/11/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/11/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/11/:/usr/lib/gcc/x86_64-linux-gnu/11/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/11/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/11/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-I' '/usr/local/include' '-g' '-static' '-o' 'boopkit' '-v' '-mtune=generic' '-march=x86-64' '-dumpdir' 'boopkit.'
/usr/lib/gcc/x86_64-linux-gnu/11/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/11/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/11/lto-wrapper -plugin-opt=-fresolution=/tmp/ccZkCooh.res -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_eh -plugin-opt=-pass-through=-lc --build-id -m elf_x86_64 --hash-style=gnu --as-needed -static -z relro -o boopkit /usr/lib/gcc/x86_64-linux-gnu/11/../../../x86_64-linux-gnu/crt1.o /usr/lib/gcc/x86_64-linux-gnu/11/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/11/crtbeginT.o -L/usr/lib/gcc/x86_64-linux-gnu/11 -L/usr/lib/gcc/x86_64-linux-gnu/11/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/11/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/11/../../.. -lbpf -lelf -lpcap -lpthread /tmp/ccJQGe9q.o /tmp/ccmNmmR6.o /tmp/cct0qgmh.o "" --start-group -lgcc -lgcc_eh -lc --end-group /usr/lib/gcc/x86_64-linux-gnu/11/crtend.o /usr/lib/gcc/x86_64-linux-gnu/11/../../../x86_64-linux-gnu/crtn.o
/usr/bin/ld: cannot find : No such file or directory
collect2: error: ld returned 1 exit status
```

All the static lib file are in the right path.
```
k8s@k8s:~/boopkit$ locate libbpf.a
/usr/lib/x86_64-linux-gnu/libbpf.a
/usr/src/linux-headers-5.15.0-25-generic/tools/bpf/resolve_btfids/libbpf/libbpf.a
/usr/src/linux-headers-5.15.0-27-generic/tools/bpf/resolve_btfids/libbpf/libbpf.a
k8s@k8s:~/boopkit$ locate libpcap.a
/usr/lib/x86_64-linux-gnu/libpcap.a
k8s@k8s:~/boopkit$ locate libelf.a
/usr/lib/x86_64-linux-gnu/libelf.a
k8s@k8s:~/boopkit$ locate libc.a
/usr/lib/x86_64-linux-gnu/libc.a
/usr/lib32/libc.a
/usr/libx32/libc.a
k8s@k8s:~/boopkit$ locate libpthread.a
/usr/lib/x86_64-linux-gnu/libpthread.a
/usr/lib32/libpthread.a
/usr/libx32/libpthread.a



```

---

### Post by QIII on 2022-06-11
I have restored the content of your post.  We consider deletion of post contents to be be forums vandalism or defacement.

If you found a solution, please be so kind as to share it with the community so others may find a solution to a similar problem.

---

### Post by #&amp;thj^% on 2022-06-11
These Dependentices are needed

eBPF and Loader Compile-Time Dependencies
[list]
    [*]‘clang’
    [*]‘linux-headers’
    [*]‘llvm’
    [*]‘libbpf’
    [*]‘lib32-glibc’[/list]

    Boopkit runtime dependencies
[list]
    [*]Linux kernel with eBPF enabled/supported
    [*]Ncat running on the server
    [*]Root access[/list]

This pertains to eBPF: [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/BHI](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/BHI) 
To help mitigate this new attack and to guard against any future possible privilege escalation attacks via eBPF, the ability for unprivileged users to load eBPF code into the kernel has now been disabled by default on Ubuntu 22.04 LTS 20.04 LTS, Ubuntu 18.04 LTS and Ubuntu 16.04 ESM as well.

Admins can re-enable this ability if needed it via sysctl 7:

 ```
sudo sysctl kernel.unprivileged_bpf_disabled=0

```
Admins can disable unprivileged eBPF until the next boot via:

 ```
sudo sysctl kernel.unprivileged_bpf_disabled=1

```
Admins can disable it, but allow it to be re-enabled by an admin without rebooting, via:

```
 sudo sysctl kernel.unprivileged_bpf_disabled=2
```

To see the current status of unprivileged eBPF, do:

```
 sysctl kernel.unprivileged_bpf_disabled

```
A result value of 1 or 2 indicates that unprivileged eBPF is disabled.   
I thought I would just let you know if you did not already.

---

### Post by Skaperen on 2022-10-28
did you check to verify what might be at that file location?
```

ls -dl /usr/bin/ld

```
maybe there is a dangling symlink.  maybe there is a file with a #! referring to a missing interpreter.  maybe your [FONT=courier new]/etc/ld.so.cache[/FONT] is out of date.  many things gone weirdly wrong can cause that error message.

---

