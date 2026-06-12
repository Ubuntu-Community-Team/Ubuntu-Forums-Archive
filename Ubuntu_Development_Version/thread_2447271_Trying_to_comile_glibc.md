---
title: "Trying to comile glibc"
date: 2020-07-16
forum: Ubuntu Development Version
---

### Post by rafimoor on 2020-07-16
Hi,

I am trying to make my own changes to glibc. I've downloaded debian source tar file and opened it, but there is no configure script in it nor any README or INSTALL files with instruction for building the package.
I've also downloaded the package from Ubuntu with apt source, there is a debian directory there, but I couldn't find a way to configure it to use the content of this directory.

How can I build glibc that can be used to replace Ububtu glibc?

Thanks

---

### Post by dino99 on 2020-07-16
Dont you got a 'makefile' ? then do a 'make' from its path

[http://www.linuxfromscratch.org/lfs/view/stable/chapter05/glibc.html](http://www.linuxfromscratch.org/lfs/view/stable/chapter05/glibc.html)

---

### Post by mc4man on 2020-07-16
Any source file of glibc has a configure in it, guess you didn't look closely or didn't get the source..
Package building of a source is driven via the debian folder, not source.
To build and install the glibc source without debian/ubuntu patches and without doing as a set of packages will likely be the end of a useful install.
Try the /debian/rules file for changes..

---

### Post by rafimoor on 2020-07-17
The package I've got by apt source includes Ubuntu patches.
I can configure and compile it with some prefix, and then install and use it from the prefix directory. But I can't use it as the primary glibc, because glibc.so is linked to ld-linux-linux-x86-64.so.2 in the wrong directory and the hardcoded search path in ld-linux-linux-x86-64.so.2 is also not like in the one of Ubuntu. Here are header files created during compilation. (ignore the prefix /tmp/aaa I used for test comilation):

runtime-linker.h:

#define RUNTIME_LINKER "/tmp/aaa/lib/ld-linux-x86-64.so.2"

trusted-dirs.h:
#define SYSTEM_DIRS \
  "/tmp/aaa/lib/" "\0" "/lib/" "\0" "/tmp/aaa/lib/"
#define SYSTEM_DIRS_LEN \
  13, 5, 13
#define SYSTEM_DIRS_MAX_LEN     13
#define DL_DST_LIB "tmp/aaa/lib"


It doesn't seem to use the rules and sysdeps from the debian directory.

I've also traced the compilation with strace, and there is no open, or chdir to this directory. I've tried all kinds of switches to the configure script - no success.

Thanks

---

### Post by rafimoor on 2020-07-27
I'm sure this is not the right way to do it, but this build libraries that work:

../glibc-2.27/configure --prefix="" --libdir=/lib/x86_64-linux-gnu --build=x86_64-linux-gnu
make -j 4 rtlddir=/lib64 extra_libdir="" slibdir=/lib/x86_64-linux-gnu user-defined-trusted-dirs=/usr/lib/x86_64-linux-gnu

---

### Post by monkeybrain20122 on 2020-07-27
> **rafimoor said:**
> The package I've got by apt source includes Ubuntu patches.
I can configure and compile it with some prefix, and then install and use it from the prefix directory. But I can't use it as the primary glibc, because glibc.so is linked to ld-linux-linux-x86-64.so.2 in the wrong directory and the hardcoded search path in ld-linux-linux-x86-64.so.2 is also not like in the one of Ubuntu. Here are header files created during compilation. (ignore the prefix /tmp/aaa I used for test comilation):



You can't link it with just LD_LIBRARY_PATH. It is probably off topic since I don't know why you do this, but I have  compiled glibc2.27 on Ubuntu 16.04 for one third party app that requires it.

 In order to change the hard link in the binary (it doesn't provide source code) I use this [https://github.com/NixOS/patchelf](https://github.com/NixOS/patchelf) and it worked like a charm. But then you'll have to use LD_LIBARARY_PATH to load things that are in /lib/x86_64-linux-gnu/ EXCEPT ld-linux-linux-x86-64.so.2 since this directory won't be found anymore (so copy .so files from  /lib/x86_64-linux-gnu/ that you need to run the app EXCEPT ld-linux-linux-x86-64.so.2 s to a new directory and add that new directory to LD_LIBRARY_PATH)

---

### Post by rafimoor on 2020-07-30
I'm just trying to get the same configuration of the libraries as the original libraries in Ubuntu 18.04 distribution, so that I can replace them with my version without any other change.

In Ubuntu 18.04, libc.so.6 is locates at /lib/x86_64-linux-gnu/ and is a link to libc-2.27.so in the same directory:

# locate libc.so.6 | grep -v snap
/lib/i386-linux-gnu/libc.so.6
/lib/x86_64-linux-gnu/libc.so.6
# ls -l /lib/x86_64-linux-gnu/libc.so.6
lrwxrwxrwx 1 root root 12 Jun  4 20:25 /lib/x86_64-linux-gnu/libc.so.6 -> libc-2.27.so


libc-2.27.so is linked against /lib64/ld-linux-x86-64.so.2:

# ldd /lib/x86_64-linux-gnu/libc-2.27.so
    /lib64/ld-linux-x86-64.so.2 (0x00007fe7c813f000)
    linux-vdso.so.1 (0x00007fff15cde000)

/lib64/ld-linux-x86-64.so.2 is a link to /lib/x86_64-linux-gnu/ld-2.27.so:

ls -l /lib64/ld-linux-x86-64.so.2
lrwxrwxrwx 1 root root 32 Jun  4 20:25 /lib64/ld-linux-x86-64.so.2 -> /lib/x86_64-linux-gnu/ld-2.27.so

The hardcoded path in ld-2.27.so can be found by tracing a program with strace or (apperently) by using strings:

# strings /lib/x86_64-linux-gnu/ld-2.27.so | grep /lib | head -15
/lib/x86H3N
/usr/libH3N
>/lib
/usr/libH9
/lib/x86I3R
/usr/libI3R
:/lib
/usr/libI9
[SIZE=4][B][COLOR=#ff0000]/lib/x86_64-linux-gnu/
/usr/lib/x86_64-linux-gnu/
/lib/
/usr/lib[/COLOR]/[/B][/SIZE]
This program usually lives in the file `/lib/ld.so', and special directives

I'm sure there is easier way then what I've used. After all it is done in the Ubuntu build of the distribution.

---

