---
title: "Exchange EWS install error 12.04"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by seebach on 2012-03-24
Hi,

I'm trying to install Exchange EWS plugin on my asus zenbook, on which i run 12.04 because of the improved hardware support. The package comes from:
[https://launchpad.net/~phurley/+archive/ppa/+build/3099782]("https://launchpad.net/%7Ephurley/+archive/ppa/+build/3099782")

I get the following error from dpkg:

```
dpkg: dependency problems prevent configuration of evolution-ews:
 evolution-ews depends on libebook1.2-12 (>= 3.2.2); however:
  Package libebook1.2-12 is not installed.
 evolution-ews depends on libecal1.2-10 (>= 3.2.2); however:
  Package libecal1.2-10 is not installed.
 evolution-ews depends on libedataserver1.2-15 (>= 3.2.2); however:
  Package libedataserver1.2-15 is not installed.

```But all the above packages are installed, anyone got an idea, help please?

---

### Post by mörgæs on 2012-03-24
Moved to the development forum.

---

### Post by dcstar on 2012-03-25
> **seebach said:**
> Hi,

I'm trying to install Exchange EWS plugin on my asus zenbook, on which i run 12.04 because of the improved hardware support. The package comes from:
[https://launchpad.net/~phurley/+archive/ppa/+build/3099782]("https://launchpad.net/%7Ephurley/+archive/ppa/+build/3099782")
..........

That PPA specifically says that the package is for Oneric (11.10), not 12.04.

[http://itworks.hu/2012/03/06/compiling-evolution-ews-for-ubuntu-12-04/](http://itworks.hu/2012/03/06/compiling-evolution-ews-for-ubuntu-12-04/)

---

### Post by NHclimber on 2012-03-26
I'll repackage it after Precise is released.

---

