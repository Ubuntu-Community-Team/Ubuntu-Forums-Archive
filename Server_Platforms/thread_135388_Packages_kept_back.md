---
title: "Packages kept back"
date: 2006-02-23
forum: Server Platforms
---

### Post by Iowan on 2006-02-23
While doing the apt-get update/upgrade , I'm informed that "the following packages have been kept back:  linux-image-386 linux-restricted-modules-386."  This process upgraded the kernel on my workstation, but not the server.  Why are they held back?  How (or SHOULD) I "un-keep back" them?

Oh, as a sidenote, once a new kernel is installed, what's the proper way to clean out the old one?

---

### Post by oakz on 2006-02-23
packages are "kept back" when they depend on other packages that you don't already have installed (upgrade will not install new dependent packages)

To fix this, either do a dist-upgrade, or install the listed packages, which should automatically install their dependencies.

To clean out an old kernel package, just remove it, either through the command line or synaptic.

---

