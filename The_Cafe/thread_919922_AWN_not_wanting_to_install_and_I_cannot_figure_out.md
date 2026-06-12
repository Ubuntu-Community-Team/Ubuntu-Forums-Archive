---
title: "AWN not wanting to install and I cannot figure out how to make it"
date: 2008-09-14
forum: The Cafe
---

### Post by Lord Xeb on 2008-09-14
nathan@nathan-laptop:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr482.1~hardy) but it is not going to be installed
                              Depends: libcairo2 (>= 1.6.0) but 1.4.10-1ubuntu4.4 is to be installed
                              Depends: libgnome-desktop-2 (>= 1:2.22) but 1:2.20.1-0ubuntu1 is to be installed
                              Depends: liborbit2 (>= 1:2.14.10) but 1:2.14.9-0ubuntu1 is to be installed
                              Depends: libpango1.0-0 (>= 1.20.5) but 1.18.3-0ubuntu1 is to be installed
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libcairo2 (>= 1.6.0) but 1.4.10-1ubuntu4.4 is to be installed
                        Depends: libglib2.0-0 (>= 2.16.0) but 2.14.1-1ubuntu1 is to be installed
                        Depends: libgnome-desktop-2 (>= 1:2.22) but 1:2.20.1-0ubuntu1 is to be installed
                        Depends: liborbit2 (>= 1:2.14.10) but 1:2.14.9-0ubuntu1 is to be installed
                        Depends: libpango1.0-0 (>= 1.20.5) but 1.18.3-0ubuntu1 is to be installed
                        Depends: libtrackerclient0 (>= 0.6.6) but 0.6.3-0ubuntu3 is to be installed
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed
E: Broken packages


What is going on here?

---

### Post by tuxxy on 2008-09-14
Just a thought, have you checked your sources.list isnt commented or something

[http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by zmjjmz on 2008-09-14
> **Lord Xeb said:**
> nathan@nath [stuff] ng on here?

Have you tried finding python-awn-bzr?

---

