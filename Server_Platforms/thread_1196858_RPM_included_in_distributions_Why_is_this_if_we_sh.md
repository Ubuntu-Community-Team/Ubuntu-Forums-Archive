---
title: "RPM included in distributions: Why is this if we should use Alien?"
date: 2009-06-25
forum: Server Platforms
---

### Post by aldous on 2009-06-25
I've always installed deb packages when available and RPM packages only when DEB packages are unavailable.  I've always used the alien utility to convert the RPM packages to DEBs...it's the standard way to do it.

Yet, somewhere along the way, the Red Hat Package manager started showing up in my Ubuntu distribution.  You can install RPMs simply by running rpm on the command line, just as if you were on RedHat/Fedora/Centos.  But nobody recommends that you do this.  The Google tells us that we should all continue to use alien to convert debs to RPMs when we must.

In fact, there is a note in the package manager details for most versions of Ubuntu for the Redhat Package Manager that says:

"If you want to install Red Hat Packages then please use the alien package. Using rpm directly will bypass the Debian packaging system!"

So my question is, why is the Red Hat Package manager included in the Ubuntu distribution?

---

### Post by 67GTA on 2009-06-25
RPM is a dependency of alien. It installs it when you install alien. It is not installed by default. Alien can convert deb to rpm, and rpm to deb, plus convert to/from LSB, Solaris, and Slackware packages. If you install an rpm package with rpm on a Debian based system, it will likely not put the files in the right places for proper Debian integration.

---

