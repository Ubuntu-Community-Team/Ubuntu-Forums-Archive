---
title: "Missing x32 libraries"
date: 2018-06-30
forum: Ubuntu Application Development
---

### Post by mkwa2 on 2018-06-30
I try to build a program for x32 model (that is, using  gcc with -mx32 flag). A simple "hello" x32 program builds and works fine. But my program uses libreadline.so (and other libs), and I cannot find them for x32 model.

For the older i386 model (using gcc -m32 ...), I install the i386 version of libreadline by command

apt install libreadline-dev:i386

How do I install the x32 version of libreadline?

---

