---
title: "Warning: prerequisite Digest::SHA1 0 not found."
date: 2010-10-07
forum: Server Platforms
---

### Post by killer50stang on 2010-10-07
This is installed and I get this error.  I am attempting to install razor-agents 2.84 and get this error along with:

Warning: prerequisite URI::Escape 0 not found.

Both of these were install in CPAN.  When I attempt to install them again, they say they are up to date.  Any ideas?

---

### Post by SeijiSensei on 2010-10-07
Try installing from the repositories and see if it helps.  For instance, Digest::SHA1 is part of this package: [http://packages.ubuntu.com/lucid/libdigest-sha1-perl](http://packages.ubuntu.com/lucid/libdigest-sha1-perl)

---

### Post by killer50stang on 2010-10-07
> **SeijiSensei said:**
> Try installing from the repositories and see if it helps.  For instance, Digest::SHA1 is part of this package: [http://packages.ubuntu.com/lucid/libdigest-sha1-perl](http://packages.ubuntu.com/lucid/libdigest-sha1-perl)

so I can apt-get install these?  Guess I need an example... I tried to apt-get install from the link above and they are already installed.

---

### Post by killer50stang on 2010-10-08
Tried this too:

apt-get install libdigest-sha1-perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
libdigest-sha1-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded

---

### Post by killer50stang on 2010-10-11
anyone?

---

### Post by killer50stang on 2010-10-13
Bump.

---

