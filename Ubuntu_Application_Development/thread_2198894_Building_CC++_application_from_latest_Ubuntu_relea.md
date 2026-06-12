---
title: "Building C/C++ application from latest Ubuntu release to LTS and avoid probl w/ glibc"
date: 2014-01-11
forum: Ubuntu Application Development
---

### Post by npequeux-g on 2014-01-11
Hi all,

I have seen this question in some forum but no answer until now.
Developers want to use latest release of ubuntu (today 13.10) but target platform (customer,...) should be using a more stable and maintened release i.e. : LTS.
But when simply, compiling with gcc/g++ 4.6 , you fall to GLIBC issue with requesting 2_17 instead of 2_15 etc,.....

A good solution in my opinion should be to use a "cross" compilation toolchain, and the best should be to use exactely the same that the standard LTS one.
But I didn't see it anywhere.... Only remaining solution is to fallback to building an as close as possible toolchain with tools like crosstool-ng,...

An other workaround should be to compile our application with an non standard libc and then launch with an LD_LIBRARY_PATH but that will forbit the application to launch any native LTS application without risk.

So my question  : How to get that toolchain ? Or is there an other solution ?


Best regards
Nicolas Péqueux

---

