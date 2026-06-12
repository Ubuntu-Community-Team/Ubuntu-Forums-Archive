---
title: "F-spot 0.4.0"
date: 2007-09-16
forum: Repositories &amp; Backports
---

### Post by Foxmike on 2007-09-16
Hi!  I successfully compiled the latest f-spot source (0.4.0) under ubuntu feisty for it looks very promising.  I've built a .deb package with checkinstall but it won't install because it tries to replace a gcc-4.1 library (/usr/lib/gcc/i486-linux-gnu/4.1.2/crtbeginS.o).

Did I did something wrong?

Thanks for help!:)

-FM

---

### Post by engla on 2007-09-16
checkinstall is not so easy to work with; there are other "easy" ways to create debs.

This is basically how you backport and application:
Go to packages.ubuntu.com and find the right package and version there.
Download the source package; that is the .dsc file, the .tar.gz file and the .diff.gz file if it exists.

Run "dpkg-source -x file.dsc" to unpack the whole source library. cd into the source directory and run "dpkg-buildpackage -rfakeroot".

That's all of it.. :) You have to install some debian maintainer tools from the repo as well as that 'fakeroot'.

With this method, if it is successful, you make "perfect" .debs -- as good as if they came from the ubuntu repository. (save the testing if it comes from gutsy)

---

### Post by Foxmike on 2007-09-16
Thank you very much!  I'll definately try this method.

---

### Post by Foxmike on 2007-09-16
Ok it worked flawlessly!  Thanks again for the help!:)

---

### Post by sassur on 2007-09-17
I would use [prevu]("https://wiki.ubuntu.com/Prevu"), with prevu you can backport a lot of packages from Gutsy to Feisty, Edgy etc.

---

### Post by Foxmike on 2007-09-18
Just for the info, f-spot-0.4.0-ubuntu2 is out, compiles well and has nice bug fixes!!! I just tried it out on feisty and everything seems to work fine so far!:)

---

