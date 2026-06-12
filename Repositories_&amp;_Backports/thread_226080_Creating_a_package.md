---
title: "Creating a package"
date: 2006-07-30
forum: Repositories &amp; Backports
---

### Post by tibbe on 2006-07-30
After reading the excruciating long and over complicated process for creating a .deb package at [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/) (note: I'm not complaining about the guide but the process itself) thinking that there must be a better way. Surely, if I can install my OS using a six step process I ought to be able to create a package without downloading a dozen packages, following a not to clear and brittle build process.

What I want is a package for Neko ([http://nekovm.org]("http://nekovm.org")). I've written a little manual install procedure:

To install Neko on Ubuntu 6.06 LTS perform the following steps:

1. Download Neko 1.3:
```
$ wget http://nekovm.org/_media/neko-1.3-src.tar.gz
```

2. Extract the files:
```
$ tar zxf neko-1.3-src.tar.gz
```

3. Build the binaries/library
```
$ cd neko-1.3-src
(Press 's' if asked to install a library, these are optional.)
$ make
(Running the test is not strictly necessary but it's a sane thing to do.)
$ make test
```

4. Copy the binaries to /usr/bin
```
$ sudo cp bin/neko /usr/bin
$ sudo cp bin/nekoc /usr/bin
$ sudo cp bin/nekotools /usr/bin
```

5. Install libraries
```
$ sudo mkdir -p /usr/lib/neko
$ sudo cp bin/libneko.so /usr/lib
$ sudo cp bin/*.ndll /usr/lib/neko
```

Done. You can now delete the archive downloaded in step one and the
directory created by unpacking the source in step two if you want to.

To uninstall simply do:
```
$ sudo rm -i /usr/bin/neko /usr/bin/nekoc /usr/bin/nekotools /usr/lib/libneko.so /usr/lib/neko/*
$ sudo rmdir /usr/lib/neko
```

I realize that there's some more information that needs to go in a package like:
[LIST]
[*]some man files
[*]package dependencies (there's only one: libgc)
[*]a description and version number
[/LIST]

Is there a way to create a package without leaving me crying? I don't think checkinstall is the way to go either (it's an adhoc hack).

---

### Post by OpsVentus on 2006-07-31
Something like this?
[http://www-128.ibm.com/developerworks/linux/library/l-debpkg.html?ca=dgr-lnxw01DebianLinux](http://www-128.ibm.com/developerworks/linux/library/l-debpkg.html?ca=dgr-lnxw01DebianLinux)

I couldn't find the howto I used to set up the packaging for my programs. But this looks the same.

Good luck,
Bart.

---

### Post by quvil on 2006-08-01
> **tibbe said:**
> 
Is there a way to create a package without leaving me crying?
You may want to look at Ubuntu's guide for creating packages - it is shorter, Ubuntu specific and (it seems to me) simpler and clearer than Debian's packaging guide:


[https://help.ubuntu.com/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/ubuntu/packagingguide/C/index.html)

---

### Post by loell on 2006-08-01
the thing is, there are programs that are easy to package, and there are also programs that's complicated to package.

---

