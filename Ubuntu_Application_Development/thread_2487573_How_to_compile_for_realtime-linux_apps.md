---
title: "How to compile for realtime-linux apps"
date: 2023-06-08
forum: Ubuntu Application Development
---

### Post by duncanmclean on 2023-06-08
Hello,

I've used ubuntu pro to install the realtime kernel. That appears to have worked properly. Now I'm trying to compile a program that makes use of the realtime kernel. My sample program is failing to compile because of:

#include <rtl_sched.h>

This header is not being found. I've searched my system and cannot find this header anywhere. Is there something else I should be installing after running "pro enable realtime-kernel".

Thanks for the help!

---

### Post by TheFu on 2023-06-09
Typically, there are development package versions and non-development package versions.  I suspect you need to install the development versions. That's common across all Linuxen.

So, for kernels, you'll need the specific kernel version and the specific header files for that kernel installed.

I don't have a real-time kernel (I did realtime flight control programming many decades ago, but we didn't use Unix). Anyway, Ubuntu has meta-packages that point to specific versions of things.

I'm running kernel 5.15.0-73. To see all the related packages, 
```
$ dpkg -l '*5.15.0-73*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version      Architecture Description
+++-======================================-============-============-========================>
ii  linux-headers-5.15.0-73                5.15.0-73.80 all          Header files related to >
ii  linux-headers-5.15.0-73-generic        5.15.0-73.80 amd64        Linux kernel headers for>
ii  linux-image-5.15.0-73-generic          5.15.0-73.80 amd64        Signed kernel image gene>
un  linux-image-unsigned-5.15.0-73-generic <none>       <none>       (no description availabl>
ii  linux-modules-5.15.0-73-generic        5.15.0-73.80 amd64        Linux kernel extra modul>
ii  linux-modules-extra-5.15.0-73-generic  5.15.0-73.80 amd64        Linux kernel extra modul

```
Clear as mud?
You'd see the real-time kernel+version and would need to ensure the headers and modules for that same kernel version are installed. If that doesn't install the header file you need, IDK the answer.

If you use re-entrant code and multiple threads, be very careful.  Even the best programmers following all the best practices get caught with race conditions and data homogeneity problems.  I've had MT, reentrant code get through multiple, formal, code reviews, and run for 6 months, before issues started showing up at client locations.

---

### Post by duncanmclean on 2023-06-14
Thanks for the reply. I found out that at least part of my problem was using very old examples that no longer worked. Moving to more up-to-date samples that used new header names allowed me to get much farther.

Thanks!

---

