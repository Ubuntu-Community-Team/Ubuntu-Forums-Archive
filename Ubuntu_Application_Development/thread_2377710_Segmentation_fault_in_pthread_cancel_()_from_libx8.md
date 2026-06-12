---
title: "Segmentation fault in pthread_cancel () from /lib/x86_64-linux-gnu/libpthread.so.0"
date: 2017-11-16
forum: Ubuntu Application Development
---

### Post by poshiya on 2017-11-16
We have 32Bit driver code. We are able to compile 32Bit driver code in 64Bit machine successfully.


We have a console application which will pass "User ISR function" from application layer to kernel. The ISR will be called by kernel in kernel thread. The thread is created successfully but while terminating the application we are facing error like **"Segmentation fault in pthread_cancel ()"**.
[B]
dmesg Log:[/B]  **segfault** at ffffffff853879d0 ip 00007ffe8575506d sp 00007fff76fc1490 error 5 in **libpthread-2.15.so**[7ffe85748000+18000]

If you need more information feel free to ask me.

---

### Post by poshiya on 2017-11-17
dmesg Log: **segfault** at ffffffff853879d0 ip 00007ffe8575506d sp 00007fff76fc1490 error 5 in **libpthread-2.15.so**[7ffe85748000+18000]

---

