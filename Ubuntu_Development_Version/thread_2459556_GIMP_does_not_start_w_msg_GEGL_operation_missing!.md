---
title: "GIMP does not start w msg GEGL operation missing!"
date: 2021-03-21
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-03-21
After recent updates:
GIMP does not start with msg: GEGL operation missing!
GIMP requires the GEGL operation "gegl:introspect".
This operation cannot be found. Check your
GEGL install and ensure it has been compiled
with any dependencies required for GIMP.

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1920668](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1920668)

---

### Post by dino99 on 2021-03-22
Should works better now :D

gimp (2.10.22-3) unstable; urgency=medium

  * debian/control.in: Add graphviz to the dependencies.
    Some optional functionality of libgegl used in gimp now requires the dot
    executable shipped in the graphviz package (Closes: #985317)
  * debian/patches/02_hurd_ftbfs.patch: Fix FTBFS on hurd-i386.
    Thanks to Svante Signell <ss@aaa.com> (Closes: #934077)

 -- Laurent Bigonville <xx@zz.org>  Sat, 20 Mar 2021 12:21:08 +0100

---

### Post by guiverc on 2021-03-22
I saw discussion on this when I looked at my PC this morning (#ubuntu-quality *I believe*), but couldn't recall where I saw it the night before (*most likely this thread*)

Thanks for noticing it @corradoventu, reporting it, and helping make Ubuntu better :)

---

### Post by corradoventu on 2021-03-22
Problem solved by new GIMP 2.10.22-3 arrived half an hour ago

---

