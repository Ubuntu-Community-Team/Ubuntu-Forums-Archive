---
title: "Quantal open for development"
date: 2012-04-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by novatillasku on 2012-04-30
Quantal is now open for development.

Matthias Klose announce: [https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035152.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035152.html")

"Quantal is now open for development, with syncs from unstable starting shortly.
 The development version starts with updated versions of GCC and OpenJDK, some
soname changes (boost, hdf5), and some changes with setting the build flags for
package builds. We are finally targeting Python3 as the
only Python version on the ISO/installation images.

 - GCC 4.7 is now the default, introducing some build failures caused
   by unknown compiler options, and more C++ strictness. Hints how to fix
   packages can be found at [1].  Bug reports for packages are not yet
   filed directly in Launchpad, but can be found on the Debian BTS instead [2].

 - OpenJDK 7 is now used as the default, replacing OpenJDK 6, introducing
   some build failures. The build status can be tracked at [3], open issues
   are tracked at [4].

 - Removing build flags exported from dpkg-buildpackage for quantal will
   get us in sync with Debian. Implications and fixes are discussed
   on the ubuntu-devel ML [5].

 - Python 3 is now again part of a minimal chroot on quantal, and will
   be the only Python version provided on the ISO/installation images
   for quantal.  Packages which need updates and ports for Python 3
   are tracked at [6]

Please check your uploads in a quantal chroot, don't just test in a precise
environment. See [7] how to setup such a development chroot."

---

### Post by Mathor on 2012-04-30
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035153.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035153.html)

Colin Watson-

"One thing to note: merge-o-matic is not currently operational in a useful way due to hardware trouble (it's showing data at the moment, but dating from April; attempting to run MoM causes the system to reboot). James Troup was looking into this at the end of last week, but it may take a few days yet.  Sorry for the inconvenience.

---

### Post by dnewkirk on 2012-05-01
I find the possibility of python 3 being the default install pretty exciting. Should make the testing much more fun :).

---

