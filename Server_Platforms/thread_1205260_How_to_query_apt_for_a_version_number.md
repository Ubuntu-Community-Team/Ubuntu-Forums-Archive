---
title: "How to query apt for a version number"
date: 2009-07-05
forum: Server Platforms
---

### Post by shebangs on 2009-07-05
Okay, NOT as simple as the title.

I have a python-vm-builder wrapper script which is creating an i386 hardy JeOS.

In that install, it's installing a couple custom packages from a custom repository (think: automated build server).

I need to figure out a way to get the version of package 'foobar' that will be installed in the guest.

The Host OS (that has python-vm-builder) installed is completely different to the guest (which is supported in vmbuilder).

Host is amd64, 8.10 without a URL to the custom/local repository.
The VM's are i386, 8.04 (hardy) with a URL thta allows a special 'foobar' package to be installed.

Is there such thing as:
# aptitude search foobar --mirror="" --arch="" --repo="" ?

ie:  # aptitude search foobar --mirror="http://server.com/mirror" --arch="i386" --repo="hardy" --repo-dir="main"

Thanks

---

### Post by drave99 on 2009-07-07
use a 32bit jail


install the i386, 8.04 using debootstrap
then run code in the jail with schroot

---

