---
title: "Symlinks to 32 bit libraries"
date: 2012-05-08
forum: Ubuntu Dev Link Forum
---

### Post by mogeb on 2012-05-08
Hello everyone,
I am working on Ubuntu 12.04 64 bit and I want to compile an application for 32 bit systems. I am using the -m32 flag for g++, but all the linking to libraries doesn't work. 
For example, -lxslt doesn't link against libxslt. I noticed that in /usr/lib/i386-linux-gnu, there is libxlst.so.1 but no libxslt.so (wich is what the linker is looking for right?). So I created a symlink to it and now the linker works fine. 
Is it a good solution? Am I doing something wrong? And also, is this a bug with Ubuntu 12.04?
Thank you.

---

### Post by MadCow108 on 2012-05-12
the symlink is ok, but the proper solution is to install libxslt1-dev:i386
though I get some multiarch issues if I also have libxml2-dev:amd64 installed ([https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/987502]("bug 987502")), until that is resolved stick to the symlink if that works for you.

---

### Post by mogeb on 2012-05-15
> **MadCow108 said:**
> the symlink is ok, but the proper solution is to install libxslt1-dev:i386
though I get some multiarch issues if I also have libxml2-dev:amd64 installed ([https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/987502]("http://bug%20987502")), until that is resolved stick to the symlink if that works for you.
Thanks!

---

