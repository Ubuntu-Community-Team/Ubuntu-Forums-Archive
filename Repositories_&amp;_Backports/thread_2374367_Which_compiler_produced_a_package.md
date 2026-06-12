---
title: "Which compiler produced a package"
date: 2017-10-15
forum: Repositories &amp; Backports
---

### Post by TimScottz8 on 2017-10-15
Hi. I'm building a program called WRF and it specifies that I use the same compiler for its' dependencies (like NETcdf) as I use for compiling WRF. I would like to use standard installed versions of these dependencies rather than build them myself. Is there any way of finding out which compiler has been used to build these libraries ?
Thanks
Tim

---

### Post by TheFu on 2017-10-18
Welcome to the forums.

"C" language bindings are the standard for libraries used around the world the last 50-ish years.  These are compiler agnostic almost always and I've **never** seen any issues.

OTOH, C++ libraries **are** specific to the mangling of the class libraries and any C++ libraries must be linked with a close relative of the C++ compiler used to maintain the C++ interfaces.  There is good news.  A distro standardizes on the g++ release, so if you use the default g++/gcc compiler installed with the normal dev packages, then the dependencies are all good.  This is called a "tool-chain".  

The tool-chain used for a specific distro is one of the earliest decisions made. It has to be for things to work together.  Compilers used only need match at the 2nd level.  3rd level updates are only for bug fixes and shouldn't have any impact for linking.    v  A.B.C .... only "C" should change over the life of a distro.  On an Ubuntu 14.04 system, gcc v4.8.4 is current.  Any gcc v4.8.x is compatible.

For 16.04, gcc v5.4.0 is current.

---

