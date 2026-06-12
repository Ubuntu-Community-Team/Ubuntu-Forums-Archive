---
title: "Configuration script hang on checking whether a statically linked program can ..."
date: 2010-06-26
forum: Ubuntu Dev Link Forum
---

### Post by thynson on 2010-06-26
Recently, I build th binutils2.20.51 from the cvs. The build process  broken cause after I execute the configuration script, it hang on  "checking whether a statically linked program can dlopen itself".
However, It's OK in ArchLinux. So I suppose it maybe a configuration  problem or system bug.
in config.log:
......
configure:11245: checking for dlopen in -ldl
configure:11270: gcc -o conftest -O2 -fomit-frame-pointer -s  -minline-stringops-dynamically    conftest.c -ldl   >&5
configure:11270: $? = 0
configure:11279: result: yes
configure:11398: checking whether a program can dlopen itself
configure:11478: gcc -o conftest -O2 -fomit-frame-pointer -s  -minline-stringops-dynamically  -DHAVE_DLFCN_H   -Wl,--export-dynamic  conftest.c -ldl  >&5
configure:11481: $? = 0
configure:11499: result: yes
configure:11504: checking whether a statically linked program can dlopen  itself
configure:11584: gcc -o conftest -O2 -fomit-frame-pointer -s  -minline-stringops-dynamically  -DHAVE_DLFCN_H   -Wl,--export-dynamic  -static conftest.c -ldl  >&5
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../x86_64-linux-gnu/bin/ld:  /tmp/ccDGjAt2.o: in function main:conftest.c(.text+0x19): warning:  Using 'dlopen' in statically linked applications requires at runtime the  shared libraries from the glibc version used for linking
configure:11587: $? = 0**(HANG AT HERE)**

the source file of the hung program is in the attachment.
build it with gcc conftest.c -Wl,--export-dynamic -static -o conftest
Execute it by
./conftest
and it will hang up,and the CPU is very very busy.

Why this happen on ubuntu but archlinux is ok. Is there a solution?

---

### Post by lkjoel on 2010-07-18
> **thynson said:**
> Recently, I build th binutils2.20.51 from the cvs. The build process  broken cause after I execute the configuration script, it hang on  "checking whether a statically linked program can dlopen itself".
However, It's OK in ArchLinux. So I suppose it maybe a configuration  problem or system bug.
in config.log:
......
configure:11245: checking for dlopen in -ldl
configure:11270: gcc -o conftest -O2 -fomit-frame-pointer -s  -minline-stringops-dynamically    conftest.c -ldl   >&5
configure:11270: $? = 0
configure:11279: result: yes
configure:11398: checking whether a program can dlopen itself
configure:11478: gcc -o conftest -O2 -fomit-frame-pointer -s  -minline-stringops-dynamically  -DHAVE_DLFCN_H   -Wl,--export-dynamic  conftest.c -ldl  >&5
configure:11481: $? = 0
configure:11499: result: yes
configure:11504: checking whether a statically linked program can dlopen  itself
configure:11584: gcc -o conftest -O2 -fomit-frame-pointer -s  -minline-stringops-dynamically  -DHAVE_DLFCN_H   -Wl,--export-dynamic  -static conftest.c -ldl  >&5
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../x86_64-linux-gnu/bin/ld:  /tmp/ccDGjAt2.o: in function main:conftest.c(.text+0x19): warning:  Using 'dlopen' in statically linked applications requires at runtime the  shared libraries from the glibc version used for linking
configure:11587: $? = 0**(HANG AT HERE)**

the source file of the hung program is in the attachment.
build it with gcc conftest.c -Wl,--export-dynamic -static -o conftest
Execute it by
./conftest
and it will hang up,and the CPU is very very busy.

Why this happen on ubuntu but archlinux is ok. Is there a solution?
Try:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Then retry

---

