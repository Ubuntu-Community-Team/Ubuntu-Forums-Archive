---
title: "Kernel 6.5 RC (Release Candidate) Series"
date: 2023-07-10
forum: Ubuntu Development Version
---

### Post by Doug S on 2023-07-10
The kernel 6.5 release candidate series has started, with [6.5-rc1]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.5-rc1/")

I will try it shortly, but am still on 6.4-rc7, due to some ongoing testing.

EDIT: Trying it now:

```
doug@s19:~$ uname -a
Linux s19 6.5.0-rc1-stock #1142 SMP PREEMPT_DYNAMIC Mon Jul 10 17:22:40 PDT 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2023-07-27
There has been [a regression reported]("https://bugzilla.kernel.org/show_bug.cgi?id=217703") with [kernel 6.5-rc3]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.5-rc3/"), although it looks more like a thermal throttling daemon issue.

EDIT: [an interesting regression tracker]("https://linux-regtracking.leemhuis.info/regzbot/mainline/")

---

### Post by Doug S on 2023-08-28
[A related post]("https://ubuntuforums.org/showthread.php?t=2490234").

The old libc6 dependency issue again. I am still using 20.04, so I already had the issue anyway. It now applies to 22.04.

---

