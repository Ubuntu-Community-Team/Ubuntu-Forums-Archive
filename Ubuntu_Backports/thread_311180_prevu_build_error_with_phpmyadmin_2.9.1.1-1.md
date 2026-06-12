---
title: "prevu build error with phpmyadmin 2.9.1.1-1"
date: 2006-12-02
forum: Ubuntu Backports
---

### Post by earth2mark on 2006-12-02
I am trying to backport phpmyadmin 2.9.1.1-1 from feisty, since the edgy version has some serious bugs, but I'm getting the following failure:

```
Setting up debootstrap (0.3.3.0ubuntu8~edgy1) ...
Setting up pbuilder (0.155ubuntu3) ...
Setting DEBBUILDOPTS=
 -> Attempting to parse the build-deps : pbuilder-satisfydepends,v 1.28 2006/05/30 23:45:45 dancer Exp $
 -> Considering  yada (>= 0.51)
      Tried versions: 0.48
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /var/cache/prevu/edgy-debs filesystem
 -> unmounting /var/cache/prevu/src/2792 filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/2876 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

```

The "Considering  yada (>= 0.51)" error is puzzling me because that isn't a dependency of phpmyadmin, and other ports are building fine with prevu.  Is there some way around this, or does this indicate that feisty phpmyadmin will not build on edgy?

---

### Post by jetthe on 2006-12-02
> **earth2mark said:**
> 
The "Considering  yada (>= 0.51)" error is puzzling me because that isn't a dependency of phpmyadmin, and other ports are building fine with prevu.  Is there some way around this, or does this indicate that feisty phpmyadmin will not build on edgy?


Yada and po-debconf are the two build-dependencies for the source package phpmyadmin, check [http://packages.ubuntu.com/feisty/source/phpmyadmin](http://packages.ubuntu.com/feisty/source/phpmyadmin)

Try to backport yada and then running 'prevu update'.

---

### Post by earth2mark on 2006-12-02
Well, that was a great suggestion, unfortunately prevu still fails because the backported yada doesn't satisfy the dependency:

```
Setting DEBBUILDOPTS=
 -> Attempting to parse the build-deps : pbuilder-satisfydepends,v 1.28 2006/05/30 23:45:45 dancer Exp $
 -> Considering  yada (>= 0.51)
      Tried versions: 0.51~6.10prevu1 0.48
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.

```

I was able to build the package by downloading the yada source and the phpmyadmin source from feisty, and building manually with debuild.  Installs and works fine.

I wonder if there is a way to do this with prevu cleanly, so this can be backported?

---

