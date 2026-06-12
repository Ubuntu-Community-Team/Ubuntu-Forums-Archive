---
title: "Compiling PHP5 hangs on &quot;checking the maximum length of command line arguments&quot;"
date: 2006-06-14
forum: Server Platforms
---

### Post by danfluidmind on 2006-06-14
Hi all.

I'm trying to compile PHP 5.1.4 on a new Ubuntu 6.06 Server machine and the configure script hangs on the following line in the "Configuring libtool" stage:

[INDENT]checking the maximum length of command line arguments...[/INDENT]

I've installed automake1.9, autoconf, and libtool, but it still hangs.

I've compiled PHP5 on a lot of machines, both Linux and BSD, and this is the first time I've had this problem.

Anyone have any clue of what might cause this?

Thanks
--Dan

---

### Post by Randomskk on 2006-06-14
Have you installed build-essential? just out of interest.

---

### Post by danfluidmind on 2006-06-14
Hahaha. Yes. I compiled Apache with no problems at all.

---

