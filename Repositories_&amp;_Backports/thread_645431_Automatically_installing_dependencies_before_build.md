---
title: "Automatically installing dependencies before building source package"
date: 2007-12-20
forum: Repositories &amp; Backports
---

### Post by chandra on 2007-12-20
Dear Folks,

I have downloaded the .orig.tar.gz, .diff.gz and .dsc files from the web and am attempting to build a source package from them; let us call it foo. The repository is **not** an Ubuntu or Debian deb-src archive.

I have two questions:

1. How do I find out the build-dependencies for building the source package? ```
apt-get build-dep foo
``` does not work because these packages are not from a deb-src archive. Is there any command to find out the dependencies for source packages that are not from a Ubuntu/Debian archive?

2. The built package will be installed using ```
sudo dpkg -i foo*.deb
``` Is there any way to ensure that any necessary
packages are installed automatically? I guess I am looking for the dpkg equivalent of ```
sudo apt-get install -y foo
```

Thanks.

---

### Post by F-3582 on 2007-12-20
1.: dpkg-checkbuilddeps is the thing you might be looking for.

2.: The package dependencies might be handled by dpkg pretty well, I think. If not, use GDebi which will handle the dependencies. On the other hand, you might have installed them during step 1, already.

---

### Post by stroyan on 2007-12-20
As F-3582 said, dpkg-checkbuilddeps should be able to tell you which
dependencies from the .dsc file's Build-Depends: line are not installed.
If you have code that is from some other distribution there may not be
an exact match for the package names in the control file.  (And there may
be missing dependencies that are not in the ubuntu distribution at all.)

You can often find packages that will help with building C source code
by looking for packages that provide the header files the source includes.
You could start making the package and look for compiler warnings and
errors.  Or you could use a command like ```
grep -hr '^#include <' . |sort -u
``` to search for include lines.  Many include directives will refer to header 
files that you already have installed.  You can look for packages that provide missing header files using the "apt-file" command.
```
sudo apt-get install apt-file
sudo apt-file update
apt-file search somemissingheader.h
```

---

### Post by F-3582 on 2007-12-20
> **stroyan said:**
> You can often find packages that will help with building C source code
by looking for packages that provide the header files the source includes.
You could start making the package and look for compiler warnings and
errors.  Or you could use a command like ```
grep -hr '^#include <' . |sort -u
``` to search for include lines.  Many include directives will refer to header 
files that you already have installed.

Since many makefiles are built with automake, you can expect to start getting pretty self-explanatory errors during the ./configure process, already.

---

### Post by chandra on 2007-12-28
> **F-3582 said:**
> 1.: dpkg-checkbuilddeps is the thing you might be looking for.

Thanks: dpkg-checkbuilddeps was exactly what I was looking for.

> 2.: The package dependencies might be handled by dpkg pretty well, I think. If not, use GDebi which will handle the dependencies. On the other hand, you might have installed them during step 1, already.

The install dependencies are a little more difficult to handle. I am building a script to automatically install all install dependencies, but with gdebi on the command line, I get ```
This package is uninstallable
Dependency is not satisfiable: <package_name(s)>
``` regardless of whether I try gdebi with no options, or with the --non-interactive or --apt-line options. Can you please tell me what I am missing?

The alternative seems to set up a local apt repository for locally built packages and use apt-get install.

Thank you.

Chandra

---

### Post by bruce89 on 2007-12-30
In this case, it'd be better to use pbuilder to build the packages, so you don't end up with loads of -dev packages installed.

---

