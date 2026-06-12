---
title: "Roll Back Compiler or Distro?"
date: 2012-08-20
forum: Ubuntu Dev Link Forum
---

### Post by Futurian on 2012-08-20
Should I keep 12.04 and replace it's g++ compiler (4.6.3-1) with an older compiler (e.g., 4.5.2-6) that will compile the code I need to compile, or should I delete my 12.04 installation, replacing it with an 11.04 installation, which includes a compiler that works with this code?

Background: I have an extensive C++ library provided by a third party. I need to compile that library, and add some code to it. Modifying the existing library, or getting the providers to update it to work with a newer compiler are not options.

I have multiple Ubuntu installations. I'll list them here, along with the corresponding g++ version, and whether or not they will compile this code:

10.04   4.4.3-4   works

11.04   4.5.2-6   works

12.04   4.6.3-1   does not work.

I would be appreciative of any suggestions regarding how to proceed.

---

### Post by mevun on 2012-08-21
I don't know which is the better choice, but it seems that you can install the older version of gcc in parallel with the current version.

I am looking at Android development and was looking at this blog entry.
[http://blog.markloiseau.com/2012/07/how-to-compile-android-on-ubuntu-12-04/](http://blog.markloiseau.com/2012/07/how-to-compile-android-on-ubuntu-12-04/)

In that entry, the author installs gcc 4.4 (and related c++ compiler) and then does some re-linking to use it.  He suggests that it is reversible to 4.6 since the new version is not deleted.

Anyway, seems like it should be fairly quick to try out.

---

### Post by Futurian on 2012-08-21
Thanks, mevun! I'll give it a try.

---

