---
title: "TACACS_PLUS install failure"
date: 2007-04-04
forum: Server Platforms
---

### Post by Edwinrg00 on 2007-04-04
Newbie here,

I've tried installing Tac-plus via Synaptic and also via the Terminal (apt-get install tac-plus) it fails. I get this error, I don't know exactly how to correct it;

Error!
The user and group tac-plus or tacacs was not created by this package,
so you must check and change that manually before this package can be
installed.

dpkg: error processing /var/cache/apt/archives/tac-plus_1%3a4.0.4.alpha-14_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/tac-plus_1%3a4.0.4.alpha-14_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rsermilik on 2007-04-09
You correct the failure by doing what it tells you to do

Add a user named tacas belonging to the group tacas.

Open a shell (terminal) and type man adduser
Look for adding a user with login not allowed and no home directory.

---

