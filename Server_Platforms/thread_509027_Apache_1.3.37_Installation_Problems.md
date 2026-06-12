---
title: "Apache 1.3.37 Installation Problems"
date: 2007-07-24
forum: Server Platforms
---

### Post by starkana on 2007-07-24
Hello everyone, I am trying to install Apache 1.3.37 manually on Ubuntu 6.06 (server edition). If it is possible to install Apache 1.3.37 using **apt-get** please let me know now. If not, then I'll move on to my problem.

Ok, so I've downloaded the Apache 1.3.37 files from apache.org. I've installed GCC using **sudo apt-get install gcc** and then installed make using **sudo apt-get install make**. Then I run **./configure --prefix=/usr/local/apache** to being the installation process. After it checks several things here and there I receive this message: ```
** A test compilation with your Makefile configuration failed. The bellow output from the compilation test will give you an idea what is failing. Note that Apache requires an ANSI C Compiler, such as gcc.

====== Error Output for sanity check ======
cd ..; gcc -DLINUX=22 -DUSE_HSREGEX -DUSE_EXPAT -I ./lib/expat-lite -DNO_DL_NEEDED `./apaci` -o helpers/dummy helpers/dummy.c -lm
/usr/bin/ld: crt.o: No such file: No such file or directory
colledt2: ld returned 1 exit status
make *** [dummy] Error 1
====== End of Error Output ======

Aborting!
```Does anyone have a clue of what is going on? I look forward to reading your replied! :)

---

### Post by starkana on 2007-07-25
Can't anyone help me? :)

---

### Post by jtc on 2007-07-25
> **starkana said:**
> If it is possible to install Apache 1.3.37 using **apt-get** please let me know now.
Yes and no :-)

You can get a patched 1.3.34 if that will do.

---

### Post by starkana on 2007-07-25
Why not fry a brain cell and figure this out?

---

