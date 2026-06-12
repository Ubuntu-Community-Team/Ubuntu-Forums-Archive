---
title: "Kernel 6.7 RC (Release Candidate) Series"
date: 2023-11-12
forum: Ubuntu Development Version
---

### Post by Doug S on 2023-11-12
Kernel 6.7-rc1 is available from kernel.org, but as we already know [the Ubuntu mainline PPA kernel]("https://kernel.ubuntu.com/mainline/?C=N;O=D") compiles have been been broken since kernel 6.6-rc5.

There are 86 default kernel configuration changes between kernel 6.6 and kernel 6.7-rc1.

```
doug@s19:~$ uname -a
Linux s19 6.7.0-rc1-stock #1189 SMP PREEMPT_DYNAMIC Sun Nov 12 17:48:59 PST 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by IanW on 2023-11-15
Just looked at the Mainline daily build - The 6.7rc1 amd64 build succeeded, but the self-tests failed because "missing kernel header files".
```
make[1]: Entering directory '/home/kernel/COD/linux/tools/testing/selftests'

-e [1;31merror[0m: missing kernel header files.
Please run this and try again:

    cd ../../..
    make headers

make[1]: *** [Makefile:189: kernel_header_files] Error 1
make[1]: Leaving directory '/home/kernel/COD/linux/tools/testing/selftests'
make: *** [debian/rules.d/1-maintainer.mk:173: compileselftests] Error 2
```

---

### Post by Doug S on 2023-12-10
Kernel [6.7-rc5 is available]("https://kernel.ubuntu.com/mainline/v6.7-rc5/"). I missed -rc4 and was late trying -rc3.

```
doug@s19:~$ uname -a
Linux s19 6.7.0-rc5-stock #1193 SMP PREEMPT_DYNAMIC Sun Dec 10 16:39:55 PST 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by IanW on 2023-12-18
[6.7-rc6]("https://kernel.ubuntu.com/mainline/v6.7-rc6/") appears, right on schedule.

---

### Post by Doug S on 2023-12-31
Kernel [6.7-rc8]("https://kernel.ubuntu.com/mainline/v6.7-rc8/") is available. I missed -rc7 and am just compiling -rc8 now.

---

### Post by IanW on 2024-01-08
[6.7 final]("https://kernel.ubuntu.com/mainline/v6.7/") has appeared. Onward to 6.8!

---

