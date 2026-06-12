---
title: "question about bug reporting on launchpad..."
date: 2009-07-12
forum: The Cafe
---

### Post by earthpigg on 2009-07-12
is this a legitimate bug, or should i submit things like this somewhere else?

[https://bugs.launchpad.net/netbook-remix/+bug/398534](https://bugs.launchpad.net/netbook-remix/+bug/398534)
> 
_**ubuntu-netbook-remix package should disable compiz / desktop effects**_

i have seen this bug marked as 'invalid':

Netbook remix doesn't work with desktop effects enabled
[https://bugs.launchpad.net/netbook-remix/+bug/247175](https://bugs.launchpad.net/netbook-remix/+bug/247175)

specifically,

"
I'm marking this as invalid, but what I really mean is 'Can't Fix'.

This is a driver bug in that the Intel (and some others) don't support Indirect rendering for GL surfaces. There are some fixes coming up in the Intel driver soon, but again, this is nothing to do with the launcher and totally about drivers.
"

since this driver bug applies to the vast _vast_ majority of netbooks, and since the netbook remix is _intended_ for netbooks, it should simply be declared that "ubuntu-netbook-remix does not support desktop effects", and they should be disabled as part of the package install process.

if the user wants to then try re-enabling them, that is on the user.

however, by default, every effort should be made to make a package work as intended for the vast majority of users.

---

### Post by Vadi on 2009-07-12
It's not a bug to begin with - the functionality isn't implemented in the drivers, and it's not something Canonical does.

---

### Post by earthpigg on 2009-07-12
the bug would be that the install process does not disable something *known* to be broken and incompatible with the application being installed.

---

