---
title: "gaim-dev package out of sync"
date: 2005-06-08
forum: Ubuntu Backports
---

### Post by Michael R Head on 2005-06-08
the gaim-dev package in hoary-backports is at version 1.2.1, but this conflicts with the gaim package, which is at 1.3.0. This prevents the installation of third party gaim plugins or any plugin development based on the backports packages. Any chance this can be remedied?

burner@phoenix:~$ sudo apt-get install gaim-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gaim-dev: Depends: gaim (= 1:1.2.1-1~5.04ubp1) but 1:1.3.0-1~5.04ubp1 is to be installed
            Depends: gaim-data (= 1:1.2.1-1~5.04ubp1) but 1:1.3.0-1~5.04ubp1 is to be installed
E: Broken packages

---

### Post by jdong on 2005-06-08
```

jdong@delta:~$ apt-cache show gaim-dev
Package: gaim-dev
Version: 1:1.3.0-1~5.04ubp1
Priority: optional
Section: devel
Maintainer: Robert McQueen <robot101@debian.org>
Depends: gaim (= 1:1.3.0-1~5.04ubp1), gaim-data (= 1:1.3.0-1~5.04ubp1), pkg-config, libglib2.0-dev
Architecture: i386
Filename: dists/hoary-backports/main/binary-i386/gaim-dev_1.3.0-1~5.04ubp1_i386.deb

```

Hmm, really? What's your sources.list?

---

