---
title: "problems with tuncfg"
date: 2008-12-22
forum: Server Platforms
---

### Post by spynappels on 2008-12-22
Hi,
   I'm having trouble installing tuncfg. When I go to the folder containing the tuncfg.c file and Makefile and type "sudo make install", I get the following error message:

install -s -m 700 tuncfg /sbin
install: cannot run strip: No such file or directory
install: strip process terminated abnormally
make: *** [install] Error 1

but the /sbin directory is there, so what is going wrong?

Thanks for your help.
Stefan.

---

