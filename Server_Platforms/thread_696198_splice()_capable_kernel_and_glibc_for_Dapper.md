---
title: "splice() capable kernel and glibc for Dapper"
date: 2008-02-13
forum: Server Platforms
---

### Post by ptsekov on 2008-02-13
Hello,

Is there are reliable way to install a newer kernel (2.6.17+) + libc (2.5.x)  which are capable of splice() on Dapper . I am writing a streaming server software which could possibly benefit from the above system call and the underlying kernel machinery but I'd like to stick to a stable and supported system. If Dapper is not the way to get splice() support - which version would be best ? Any suggestions ?

Thanks!

---

### Post by ikonia on 2008-02-15
I'd strongly advise you not to update glibc on a dapper release.

glibc is pretty much the nuts and bolts of your whole system, so changing it can have serious consiquences. If the package is not in the repo (which it's not) I'd strongly advise you not to look at putting your own package on.

---

