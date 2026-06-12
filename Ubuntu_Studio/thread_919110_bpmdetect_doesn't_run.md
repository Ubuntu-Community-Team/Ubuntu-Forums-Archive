---
title: "bpmdetect doesn't run"
date: 2008-09-13
forum: Ubuntu Studio
---

### Post by NightFalcon on 2008-09-13
Hi everybody!

I installed the content of the .tar.bz2 of bpmdetect. But when I try to run the terminal shows:

bpmdetect: error while loading shared libraries: libtag.so.1: cannot open shared object file: No such file or directory

I have the libtaglib installed.
Any idea that might help?

Thanks

site of the project:
[http://sourceforge.net/projects/bpmdetect/](http://sourceforge.net/projects/bpmdetect/)

---

### Post by Stochastic on 2008-09-13
the file you're looking for is located in the package libtag1c2a

to find this out, all you need to do is run ```
apt-file search libtag.so.1
```

---

