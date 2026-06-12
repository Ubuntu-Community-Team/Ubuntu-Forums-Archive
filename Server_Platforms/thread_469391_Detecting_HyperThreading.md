---
title: "Detecting HyperThreading"
date: 2007-06-09
forum: Server Platforms
---

### Post by Dudsmacka2 on 2007-06-09
Is there a way to determine whether an install is successfully using a P4's Hyper Threading?

---

### Post by meatpan on 2007-06-09
Consider taking a look at the processor information that has been detected by the kernel.   This info is present in the file /proc/cpuinfo.  Under the 'flags' section you should see 'ht'.  I'm not sure if this means the kernel is taking advantage of ht.   IBM has written an article discussing ht on a linux platform, which might help you find out the exact effect (if any) of ht.  Consider following some of their benchmarks.  Here is the article:  [http://www.ibm.com/developerworks/linux/library/l-htl/](http://www.ibm.com/developerworks/linux/library/l-htl/)

---

