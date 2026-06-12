---
title: "how do I install gcc on kubuntu 15.04"
date: 2015-05-23
forum: Ubuntu, Linux and OS Chat
---

### Post by i8da-rainbow on 2015-05-23
I tried the command sudo apt-get install gcc and it installed. I can't find it anywhere and when I try to launch it through the terminal using gcc & it says        [FONT=monospace][COLOR=#000000]home@home-Aspire-X1920:~$ gcc: fatal error: no input files [/COLOR]
compilation terminated. 

but when I type gcc -v i get
[/FONT]
  ```
     [FONT=monospace][COLOR=#000000]Using built-in specs. [/COLOR]
COLLECT_GCC=gcc 
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.9/lto-wrapper 
Target: i686-linux-gnu 
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.9.2-10ubuntu13' --with-bugurl=file:///usr/share/doc/gcc-4.9/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-
4.9 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.9 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale
=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-hom
e=/usr/lib/jvm/java-1.5.0-gcj-4.9-i386/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.9-i386 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.9-i386 --with-arch-directory=i386 --with-ecj-jar=
/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-targets=all --enable-multiarch --disable-werror --with-arch-32=i686 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release -
-build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu 
Thread model: posix 
gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13)  
home@home-Aspire-X1920:~$ 

[/FONT]
```

---

### Post by wildmanne39 on 2015-05-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end. Also please  use normal fonts.
Thanks

---

### Post by cariboo on 2015-05-24
You are getting the result that you get without an input fille, you may want to have a look [here]("http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html") for more info

---

### Post by flaymond on 2015-05-24
[QUOTE=cariboo]You are getting the result that you get without an input fille[/QUOTE]

+1

gcc is a compiler, and you need to have a C file to compile. If you new to C and wanna learn it, try have a look at K&R ANSI C book. You also can compile simple C programs with make. Type 'man gcc' for manual to use gcc.

---

### Post by montag dp on 2015-05-26
As the others have said, you actually did successfully install gcc.  The issue is that any time you run gcc, it expects at least one command line argument specifying the source file that you are compiling.

Also, since you mentioned that you can't find it anywhere, the 'which' command will tell you where the binary resides.  Type

```
which gcc
```

at the command prompt and it will tell you the path.

---

