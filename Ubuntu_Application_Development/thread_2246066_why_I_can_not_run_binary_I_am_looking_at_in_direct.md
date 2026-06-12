---
title: "why I can not run binary I am looking at in directory"
date: 2014-09-28
forum: Ubuntu Application Development
---

### Post by shahin on 2014-09-28
I downloaded a copy of arm toolchain from a site called SourceyCode in the form of tar file, and after untaring the content I see the following in the bin directory readme file: 
> The executables in this directory are for internal use by the compiler
and may not operate correctly when used directly.  This directory
should not be placed on your PATH.  Instead, you should use the
executables in ../../bin/ and place that directory on your PATH.

I went to ../../bin/ and I found the file that I need, but I can not issue the command I want to run the assember. Please see below:
I am in the following directory: 
```
@ubuntu:~/toolchains/arm-2014.05/arm-none-eabi/bin$ cd ../../bin
@ubuntu:~/toolchains/arm-2014.05/bin$ ls
add.s                    arm-none-eabi-g++         arm-none-eabi-nm
arm-none-eabi-addr2line  arm-none-eabi-gcc         arm-none-eabi-objcopy
arm-none-eabi-ar         arm-none-eabi-gcc-4.8.3   arm-none-eabi-objdump
arm-none-eabi-as         arm-none-eabi-gcc-ar      arm-none-eabi-ranlib
arm-none-eabi-c++        arm-none-eabi-gcc-nm      arm-none-eabi-readelf
arm-none-eabi-c++filt    arm-none-eabi-gcc-ranlib  arm-none-eabi-size
arm-none-eabi-cpp        arm-none-eabi-gcov        arm-none-eabi-strings
arm-none-eabi-cs         arm-none-eabi-gdb         arm-none-eabi-strip
arm-none-eabi-cs-daemon  arm-none-eabi-gprof       cache
arm-none-eabi-elfedit    arm-none-eabi-ld

```

And I am trying to issue: 
```

 arm-none-eabi-as -o add.o add.s

```

But I get the following error: 

```

 bash: /home/blahblah/toolchains/arm-2014.05/bin/arm-none-eabi-as: No such file or directory

```

Why can I not issue the above command?

---

### Post by steeldriver on 2014-09-28
Is it the correct binary type for your system? what does

```

file /home/blahblah/toolchains/arm-2014.05/bin/arm-none-eabi-as

```
say?

---

### Post by shahin on 2014-09-28
Thanks. I am following the instructions given here:[http://www.bravegnu.org/gnu-eprog/hello-arm.html]("http://www.bravegnu.org/gnu-eprog/hello-arm.html") I am not sure what you mean by "what does it say". Is there a command you want me to run to findout more about it?

---

### Post by steeldriver on 2014-09-28
yes, please run the command exactly as I posted above - also please post whether your system is 32-bit or 64-bit

---

### Post by shahin on 2014-09-28
Frankly, so far this has been a very interesting project. Here is why. If you look below, I am sharing the directory structure of the package I downloaded and unziped: 
```

@ubuntu:~$ ls
arm-2014.05-28-arm-none-eabi-i686-pc-linux-gnu.tar.bz2
arm-2014.05-29-arm-none-linux-gnueabi-i686-pc-linux-gnu.tar.bz2
binutils-2.11.2.tar.gz
Desktop
Documents
Downloads
examples.desktop
gcc-2.95.3.tar.gz
gdb-5.0.tar.gz
Music
newlib-1.9.0.tar.gz
Pictures
programs
Public
Templates
toolchains
Videos
@ubuntu:~$ cd toolchains/
@ubuntu:~/toolchains$ ls
arm-2014.05
@ubuntu:~/toolchains$ cd arm-2014.05/
@ubuntu:~/toolchains/arm-2014.05$ ls
add.s  arm-none-eabi  bin  i686-pc-linux-gnu  lib  libexec  share
@ubuntu:~/toolchains/arm-2014.05$ cd arm-none-eabi/
@ubuntu:~/toolchains/arm-2014.05/arm-none-eabi$ ls
bin  include  lib  share
@ubuntu:~/toolchains/arm-2014.05/arm-none-eabi$ cd bin
@ubuntu:~/toolchains/arm-2014.05/arm-none-eabi/bin$ ls
ar  as  c++  g++  gcc  ld  nm  objcopy  objdump  ranlib  README.txt  strip
sansari@ubuntu:~/toolchains/arm-2014.05/arm-none-eabi/bin$ cd ../../bin
@ubuntu:~/toolchains/arm-2014.05/bin$ ls
add.s                    arm-none-eabi-g++         arm-none-eabi-nm
arm-none-eabi-addr2line  arm-none-eabi-gcc         arm-none-eabi-objcopy
arm-none-eabi-ar         arm-none-eabi-gcc-4.8.3   arm-none-eabi-objdump
arm-none-eabi-as         arm-none-eabi-gcc-ar      arm-none-eabi-ranlib
arm-none-eabi-c++        arm-none-eabi-gcc-nm      arm-none-eabi-readelf
arm-none-eabi-c++filt    arm-none-eabi-gcc-ranlib  arm-none-eabi-size
arm-none-eabi-cpp        arm-none-eabi-gcov        arm-none-eabi-strings
arm-none-eabi-cs         arm-none-eabi-gdb         arm-none-eabi-strip
arm-none-eabi-cs-daemon  arm-none-eabi-gprof       cache
arm-none-eabi-elfedit    arm-none-eabi-ld
@ubuntu:~/toolchains/arm-2014.05/bin$ 

```
From my home directory, I go into the unzipped package's bin directory, which does not have the assembler. But when I ```
 cd ../../bin/
``` I go in a directory, which I see the assembler binary. I do not know for the life of my where this directory is, or how else I can get to it. Maybe that is why the OS can not find it either.

---

### Post by shahin on 2014-09-28
Thanks. This may have solved the problem. The Ubuntu environment is a 64bit vm running on Winodows 7. The arm file a 32 bit file according to the output of the command you asked for: 
```
blahblah@ubuntu:~/toolchains/arm-2014.05/bin$ file arm-none-eabi-as
arm-none-eabi-as: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.16, stripped
blahblah@ubuntu:~/toolchains/arm-2014.05/bin$ 

```

---

### Post by shahin on 2014-09-28
The other potential issues I see is that the package was built for GNU linux. I figured since the commands look like Debian, I may be able to run the files on Ubuntu. Am I wrong you think?

---

### Post by shahin on 2014-09-29
This is still an outstanding question for me. Can anyone chime in? I looked online also; still don't know what is the problem with the code.

---

### Post by shahin on 2014-09-29
I found the answer to this; hope it helps someone else. I needed to install the 32bit libraries, which are: ```
lib32z1 lib32ncurses5 lib32bz2-1.0
``` I may have been able to getaway with just one of them also. I have to research it.

---

