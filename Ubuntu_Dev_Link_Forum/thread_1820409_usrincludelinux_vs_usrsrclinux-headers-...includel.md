---
title: "/usr/include/linux vs /usr/src/linux-headers-.../include/linux"
date: 2011-08-07
forum: Ubuntu Dev Link Forum
---

### Post by dudkosk on 2011-08-07
What's difference between /usr/include/linux and /usr/src/linux-headers-.../include/linux?
What relation/compatibility is there between them?
Thanks in advance!

---

### Post by mehrun on 2011-08-19
This is my question too, for forum brevity I am going to ask here just another question.

linux/autoconf.h: No such file or directory

what should I to do to eliminating this problem in a standard manner? :(
note that all kernel dependent packages are installed like headers and linux-source and ...

Best Regards

---

### Post by mehrun on 2011-08-19
Aha gotcha!

#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,33)) 
#include <generated/autoconf.h> 
#else 
#include <linux/autoconf.h> 
#endif


Obviously from 2.6.33 and later versions, autoconf.h traveled to the generated directory. :o

---

### Post by gnometorule on 2011-08-26
I'm under 2.6.32, have neither a linux nor generated folder...any ideas where related files and sub-directories migrated? (that is, no linux nor generated directories doing a root 'find' for any such directory)

---

