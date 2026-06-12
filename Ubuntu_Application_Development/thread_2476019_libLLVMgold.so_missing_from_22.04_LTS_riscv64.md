---
title: "libLLVMgold.so missing from 22.04 LTS riscv64"
date: 2022-06-14
forum: Ubuntu Application Development
---

### Post by schmidtw2 on 2022-06-14
I'm trying to build an application using clang 14.0.0 and -flto, which requires the gold linker (ld.gold) and plugin (libLLVMgold.so).  Neither is present on the system (Ubuntu 22.04 LTS, riscv64).  I have the following packages installed:

clang
clang-14
libclang-14-dev
libclang-common-14-dev
libclang-cpp14
libclang1-14
libllvm14
llvm-14
llvm-14-dev
llvm-14-linker-tools
llvm-14-runtime
llvm-14-tools

It's my understanding that llvm-14-linker-tools ought to have provided the plugin, but it didn't.  I also would have thought that the standard binutils package would have provided ld.gold. /usr/bin contains riscv64-linux-gnu-gold as a symbolic link to riscv64-linux-gnu-ld.gold, but the latter isn't present.

Is there a package I still need to install, or is this a bug in the distribution for riscv64?

Thanks!
Bill

---

### Post by schmidtw2 on 2022-06-16
FYI, after some searching I discovered that binutils does not yet accept riscv64-*-* as a supported target for gold.  So that explains why these are missing.

---

