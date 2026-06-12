---
title: "not able to cross-compile mfcuk over Linux for Windows"
date: 2019-04-25
forum: Windows
---

### Post by android2014213 on 2019-04-25
root@ashish-Inspiron-15-3567:/home/ashish/mfcuk-master# ./configure --host=x86_64-w64-mingw32 

checking for GNU libc compatible malloc... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking for memset... yes
checking for strchr... yes
checking for strtoul... yes
checking endian.h usability... no
checking endian.h presence... no
checking for endian.h... no
checking sys/endian.h usability... no
checking sys/endian.h presence... no
checking for sys/endian.h... no
checking CoreFoundation/CoreFoundation.h usability... no
checking CoreFoundation/CoreFoundation.h presence... no
checking for CoreFoundation/CoreFoundation.h... no
configure: error: "Can't locate usable header file for endianness convertions."

i am trying to cross compile mfcuk over ubuntu16.04 for windows executable (.exe).
I have installed almost all dev libraries into the system but nothing works.

---

### Post by wildmanne39 on 2019-04-25
*Thread moved to **Windows a more appropriate sub-forum since this is not about a version of Ubuntu that is in development**.*

---

