---
title: "server broken after upgrade - unmet dependencies"
date: 2011-10-15
forum: Server Platforms
---

### Post by janmyszkier on 2011-10-15
the server broke after upgrade to oneiric(11.10)

some errors i'm seeing:

'apt-get upgrade' results in:
> The following packages have unmet dependencies:
libc6 : Depends: libc-bin (=2.13-0ubuntu13) but 2.13-20ubuntu5 is to be installed
libc6-dev : Depends: libc6 (=2.13-20ubuntu5) but 2.13-0ubuntu13 is to be installed
libc6-i386 : Depends: libc6 (=2.13-20ubuntu5) but 2.13-0ubuntu13 is to be installed

So i do 'apt-get -f install' it finds new libc6 package but:
> a copy of the C library was found in an unexpected directory:
/lib/x86_64-linux-gnu/libc-2.13.so
It is not safe to upgrade c library in this situation;
please remove that copy of the C library or get it out of '/lib/x86_64-linux-gnu' and try again

but when i move the file to another location no command works afterwards and i have to boot into live cd to copy it back to mentioned location and we're going in circles

Help really appreciated

---

### Post by janmyszkier on 2011-10-15
please close, moved to desktop environments as new thread

---

