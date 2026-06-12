---
title: "Can't build anything with dkms anymore"
date: 2014-02-19
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2014-02-19
After trying to install the NVIDIA driver from upstream to test a bug and uninstalling the driver afterwards I'm having troubles to build any module like virtualbox or nvidia-331-updates with dkms. Here is the log from virtualbox:

```
DKMS make.log for virtualbox-4.3.6 for kernel 3.13.0-10-generic (x86_64)
Wed Feb 19 22:59:50 CET 2014
make: Entering directory `/usr/src/linux-headers-3.13.0-10-generic'
  LD      /var/lib/dkms/virtualbox/4.3.6/build/built-in.o
  LD      /var/lib/dkms/virtualbox/4.3.6/build/vboxdrv/built-in.o
  CC [M]  /var/lib/dkms/virtualbox/4.3.6/build/vboxdrv/linux/SUPDrv-linux.o
In file included from /var/lib/dkms/virtualbox/4.3.6/build/include/VBox/types.h:30:0,
                 from /var/lib/dkms/virtualbox/4.3.6/build/vboxdrv/linux/../SUPDrvInternal.h:35,
                 from /var/lib/dkms/virtualbox/4.3.6/build/vboxdrv/linux/SUPDrv-linux.c:31:
/var/lib/dkms/virtualbox/4.3.6/build/include/iprt/types.h:99:22: fatal error: stddef.h: No such file or directory
 #  include <stddef.h>
                      ^
compilation terminated.
make[2]: *** [/var/lib/dkms/virtualbox/4.3.6/build/vboxdrv/linux/SUPDrv-linux.o] Error 1
make[1]: *** [/var/lib/dkms/virtualbox/4.3.6/build/vboxdrv] Error 2
make: *** [_module_/var/lib/dkms/virtualbox/4.3.6/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.13.0-10-generic'

```


Here is the search for stddef.h on my system:

```
root@ubuntu:~# find / | grep 'stddef\.h'
/usr/local/wine-git/include/msvcrt/stddef.h
/usr/include/linux/stddef.h
/usr/src/linux-headers-3.13.0-10-generic/include/linux/stddef.h
/usr/src/linux-headers-3.13.0-10/include/linux/stddef.h
/usr/src/linux-headers-3.13.0-10/include/uapi/linux/stddef.h

```


And here are the include paths of gcc on my system:

```
root@ubuntu:~# gcc -xc -E -v -
Using built-in specs.
COLLECT_GCC=gcc
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.2-16ubuntu1' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.2 (Ubuntu 4.8.2-16ubuntu1) 
COLLECT_GCC_OPTIONS='-E' '-v' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -E -quiet -v -imultiarch x86_64-linux-gnu - -mtune=generic -march=x86-64 -fstack-protector -Wformat -Wformat-security
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/include"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.

```


Maybe somebody can execute the 2 commands and post the results to see if there are differences. Maybe somebody has even an idea how to fix this.

---

### Post by steeldriver on 2014-02-20
I don't have access to a box with gcc-4.8 right now, but based on what I see for gcc-4.7 I would suspect that it should be looking in /usr/lib/gcc/x86_64-linux-gnu/4.8/include - which is showing as nonexistent in your case:

```

ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/include"

```

```

COLLECT_GCC_OPTIONS='-E' '-v' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.7/cc1 -E -quiet -v -imultilib . -imultiarch x86_64-linux-gnu - -mtune=generic -march=x86-64 -fstack-protector
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.7/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
[B] /usr/lib/gcc/x86_64-linux-gnu/4.7/include
[/B] /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.7/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include

```

```

$ find /usr/lib/gcc -name 'stddef.h'
/usr/lib/gcc/x86_64-linux-gnu/4.7/include/stddef.h

```

Perhaps a reinstall of gcc (or gcc-4.8 specifically?) will help? The file itself is probably part of libgcc-4.8-dev but that should be a dependency of gcc-4.8

---

### Post by Sworddragon on 2014-02-20
> **steeldriver said:**
> The file itself is probably part of libgcc-4.8-dev but that should be a dependency of gcc-4.8

This did the trick and after installing this package all modules are building fine and I'm getting this output from gcc:

```
root@ubuntu:~# gcc -xc -E -v -
Using built-in specs.
COLLECT_GCC=gcc
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.2-16ubuntu1' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.2 (Ubuntu 4.8.2-16ubuntu1) 
COLLECT_GCC_OPTIONS='-E' '-v' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -E -quiet -v -imultiarch x86_64-linux-gnu - -mtune=generic -march=x86-64 -fstack-protector -Wformat -Wformat-security
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.

```


I'm still wondering why 2 include paths are still missing but that libgcc-4.8-dev is not a dependency anymore could be a bug.


Edit: I have now opened a bug report: [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1282758](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1282758)

---

