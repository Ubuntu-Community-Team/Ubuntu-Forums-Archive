---
title: "Howto: Install subversion 1.2.0 on hoary"
date: 2005-07-05
forum: Ubuntu Backports
---

### Post by sundancer on 2005-07-05
I just built subversion-1.2.0 using the sources from debian sid (As a dependency, you must build swig1.3-1.3.24). I will post my steps:
[list=1]
[*]Insert Debian SID sources to your /etc/apt/sources.list
```

deb http://ftp2.de.debian.org/debian sid main contrib non-free
deb-src http://ftp2.de.debian.org/debian sid main contrib non-free

```
[*]Insert the following to your /etc/apt/preferences (apt-pinning)
```

Package: *
Pin: release a=unstable
Pin-Priority: 20

```
[*]Now build swig:
```

apt-get source -t unstable swig
sudo apt-get build-dep swig
cd swig1.3-1.3.24
fakeroot dpkg-buildpackage -us -uc

```
Output should be
```

dpkg-checkbuilddeps: Unmet build dependencies: python-dev (<< 2.4)

```
This is OK, so let's start building without depchecking
```

fakeroot dpkg-buildpackage -us -uc -d

```
After building, install the .deb-files
[*] Now for subversion (if you want to build javaHL-support too, make sure to have sun-j2sdk1.5 installed)
```

apt-get source -t unstable subversion
cd subversion-1.2.0/
fakeroot dpkg-buildpackage -us -uc

```
Install the unmet dependencies manually, as I'm writing this howto after already installing these packages  ](*,) But I remember, that I had to remove libsvn0 - you should see that...
To enable javaHL, edit debian/rules:
```

# Set this variable to 'yes' to build the libsvn-javahl package.
ENABLE_JAVAHL=yes
...
ifeq ($(ENABLE_JAVAHL), yes)
  # jikes 1.22 cannot compile javahl.
  confflags += --enable-javahl --with-jdk=/usr/lib/j2sdk1.5-sun --with-jikes=/usr/lib/j2sdk1.5-sun/bin/javac
endif

```
This should work. Now build the package:
```

fakeroot dpkg-buildpackage -us -uc

```
Because of many tests, this will take some time...
Now simply install the debs and you're done  :grin: 
[/list]

This is the output after installing:
```

jan@bender:~/devel/deb$ LANG=C svn --version
svn, version 1.2.0 (r14790)
   compiled Jul  4 2005, 15:12:27

Copyright (C) 2000-2005 CollabNet.
Subversion is open source software, see http://subversion.tigris.org/
This product includes software developed by CollabNet (http://www.Collab.Net/).

The following repository access (RA) modules are available:

* ra_dav : Module for accessing a repository via WebDAV (DeltaV) protocol.
  - handles 'http' scheme
  - handles 'https' scheme
* ra_svn : Module for accessing a repository using the svn network protocol.
  - handles 'svn' scheme
* ra_local : Module for accessing a repository on local disk.
  - handles 'file' scheme

```

You can now use subclipse (Works with 0.9.31). Note that you have to use javaHL. To let eclipse recognise this, you have to add the following to the startup script:
```

-vmargs -Djava.library.path=/usr/lib

```

Then it works perfectly

---

### Post by jdong on 2005-07-07
Good for you :)


I have it installed on my system in a similar way, too... However, I can't stick it into Backports because of that swig dependency.

---

### Post by Cosmic_Crusader on 2005-09-19
I have attempted to get this working in Hoary without success.

I have followed these instructions but the version now available is 1.2.3a and fails on the compile of subversion with:> libtool: unrecognized option `-DLINUX=2'
Try `libtool --help' for more information.
make[1]: *** [subversion/bindings/swig/python/svn_client.lo] Error 1
make[1]: Leaving directory `/home/cosmic/tmp/TMP/SVN/subversion-1.2.3a/build-tree/subversion-1.2.3'
make: *** [debian/stamp-build] Error 2 
Any ideas?  Does it require a more recent version of libtool?  :(

---

### Post by sundancer on 2005-09-19
I compiled it a few days ago and it works properly. There was no problem with the compile run.
My libtool version is 1.5.6-5.

---

