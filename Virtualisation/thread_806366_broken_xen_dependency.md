---
title: "broken xen dependency?"
date: 2008-05-24
forum: Virtualisation
---

### Post by clementvii on 2008-05-24
Has anyone been able to install xen on Ubuntu Hardy?  The installer on my box fails because it can't find the xenman package.  Is there a third party repository with xenman, or is this a broken dependency?

For what it's worth, I'm a newbie on both Ubuntu and Xen, so I could easily be doing something wrong.  Here's what happens on my box:

-----Begin install ubuntu-xen-desktop-----
george@ubuntubox:/etc/apt$ sudo apt-get install ubuntu-xen-desktop
[sudo] password for george:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-xen-desktop: Depends: xenman but it is not installable
E: Broken packages
george@ubuntubox:
-----End install ubuntu-xen-desktop-----

-----Begin install xenman-----
george@ubuntubox:/etc/apt$ sudo apt-get install xenman
[sudo] password for george:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xenman is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xenman has no installation candidate
george@ubuntubox:/etc/apt$
-----End install xenman-----

---

### Post by clementvii on 2008-05-27
I've put Ubuntu Server 8.04 (Hardy) on the same box in place of Desktop, and can install the ubuntu-xen-server package without any errors or warnings.  xenman is not in the list of dependencies:

-----Begin dependency queries-----
george@ubuntubox:~$ sudo apt-cache rdepends ubuntu-xen-server
ubuntu-xen-server
Reverse Depends:
george@ubuntubox:~$ sudo apt-cache depends ubuntu-xen-server
ubuntu-xen-server
  Depends: bridge-utils
  Depends: libc6-xen
  Depends: libxen3
  Depends: linux-xen
  Depends: python-xen-3.2
  Depends: xen-docs-3.2
  Depends: xen-hypervisor-3.2
  Depends: xen-tools
  Depends: xen-utils-3.2
george@ubuntubox:~$ 
-----End dependency queries-----

---

### Post by CloneSan on 2008-06-09
ubuntu-xen-desktop != ubuntu-xen-server

For installing xenman,see: 
[https://answers.launchpad.net/ubuntu/+source/xenman/+question/31759](https://answers.launchpad.net/ubuntu/+source/xenman/+question/31759)

It short, you can get the package from:
[http://launchpadlibrarian.net/11041870/xenman_0.6-5ubuntu1_all.deb](http://launchpadlibrarian.net/11041870/xenman_0.6-5ubuntu1_all.deb)

However, ubuntu-xen-desktop installs, but fails to startup properly in X with a stack trace. Which I unfortunately can't find in my logs.

---

