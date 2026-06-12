---
title: "program cannot find shared libraries"
date: 2013-11-17
forum: Ubuntu, Linux and OS Chat
---

### Post by weather197611 on 2013-11-17
Hello, I have a program compiled on Ubuntu that is looking for files in /usr/local/lib and cannot locate them (they are there). I have set the LD_LIBRARY_PATH and also created a file in /etc/ld.so.conf.d and added the line /usr/local/lib to that file. I then sudo ldconfig...the program can still not locate the needed files. Any ideas?

---

