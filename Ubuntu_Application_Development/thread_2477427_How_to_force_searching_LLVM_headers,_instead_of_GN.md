---
title: "How to force searching LLVM headers, instead of GNU headers?"
date: 2022-07-24
forum: Ubuntu Application Development
---

### Post by jiapei100 on 2022-07-24
Hi, all:

I've been using Ubuntu 22.04.

I set up CMake for **LLVM** compilation, as follows:

 ```
CMAKE_ADDR2LINE                  /usr/bin/llvm-addr2line
 CMAKE_AR                         /usr/bin/llvm-ar
 CMAKE_ASM_COMPILER               /usr/bin/clang
 CMAKE_ASM_COMPILER_AR            /usr/lib/llvm-14/bin/llvm-ar
 CMAKE_ASM_COMPILER_RANLIB        /usr/lib/llvm-14/bin/llvm-ranlib
.....
CMAKE_CXX_COMPILER               /usr/bin/clang++
 CMAKE_CXX_COMPILER_AR            /usr/bin/llvm-ar-14
 CMAKE_CXX_COMPILER_RANLIB        /usr/bin/llvm-ranlib-14
.....
```


But, it looks when I ```
#include <cmath>
```, in which ```
#include <math.h>
```, during building, it automatically search for the **GNU header** - ```
/usr/include/c++/11/math.h
```, rather than **LLVM header** - ```
/usr/lib/llvm-14/include/c++/v1/math.h
``` . 

How can I force to use LLVM's header ONLY?

Thank you

---

### Post by #&amp;thj^% on 2022-07-25
Did you ever try daphnediane's suggestion: [https://discourse.llvm.org/t/how-to-force-searching-llvm-headers-instead-of-gnu-headers/64030](https://discourse.llvm.org/t/how-to-force-searching-llvm-headers-instead-of-gnu-headers/64030)

---

