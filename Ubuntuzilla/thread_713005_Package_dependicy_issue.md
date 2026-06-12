---
title: "Package dependicy issue"
date: 2008-03-02
forum: Ubuntuzilla
---

### Post by dnguyen411 on 2008-03-02
I just downloaded the ubuntuzilla script but ran into a problem. The script is looking for libstdc++5, but I have libstdc++6 installed.

Do I have to install libstdc++5 or is there a workaround?

---

### Post by nanotube on 2008-03-02
libstdc5 does not interfere with 6, they can coexist just fine, so just let it install. mozilla's build of firefox relies on libstdc++5, that's why it's necessary.

i have 5 and 6 both installed on my system without any problems (as do thousands of other ubuntuzilla users :) ).

---

### Post by dnguyen411 on 2008-03-03
Thanks

---

### Post by dnguyen411 on 2008-03-03
I've tried installing libstdc++5 but got this error.

dnguyen411@haruhi:~$ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate

Anybody know where I can find libstdc++5 ?

---

### Post by nanotube on 2008-03-03
> **dnguyen411 said:**
> I've tried installing libstdc++5 but got this error.

dnguyen411@haruhi:~$ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate

Anybody know where I can find libstdc++5 ?

ehrm... strange, what version of ubuntu are you running?

what's your output of  ```
apt-cache search libstdc
``` ?

libstdc++5 is included in the core repositories in feisty, at least (that's what i'm running), and i'm pretty sure on gutsy as well...

---

### Post by dnguyen411 on 2008-03-04
I'm running Gutsy

dnguyen411@haruhi:~$ apt-cache search libstdc
libstdc++6-4.1-dev - The GNU Standard C++ Library v3 (development files)
lib64stdc++6 - The GNU Standard C++ Library v3 (64bit)
libgmp3-dev - Multiprecision arithmetic library developers tools
libstdc++5 - The GNU Standard C++ Library v3
libstdc++5-3.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6 - The GNU Standard C++ Library v3
libstdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.1-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.2-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.2-doc - The GNU Standard C++ Library v3 (documentation files)
lib64stdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
libg++2.8.1.3-dbg - The GNU C++ extension library - debugging files
libstdc++2.10-dbg - The GNU stdc++ library (debugging files)
libstdc++2.10-dev - The GNU stdc++ library (development files)
libstdc++2.10-glibc2.2 - The GNU stdc++ library
libstdc++5-3.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++5-3.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++5-3.3-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.1-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.2-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-pic - The GNU Standard C++ Library v3 (shared library subset kit)

---

### Post by nanotube on 2008-03-04
> **dnguyen411 said:**
> I'm running Gutsy

dnguyen411@haruhi:~$ apt-cache search libstdc
libstdc++6-4.1-dev - The GNU Standard C++ Library v3 (development files)
lib64stdc++6 - The GNU Standard C++ Library v3 (64bit)
libgmp3-dev - Multiprecision arithmetic library developers tools
**libstdc++5 - The GNU Standard C++ Library v3**
libstdc++5-3.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6 - The GNU Standard C++ Library v3
libstdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.1-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.2-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.2-doc - The GNU Standard C++ Library v3 (documentation files)
lib64stdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
libg++2.8.1.3-dbg - The GNU C++ extension library - debugging files
libstdc++2.10-dbg - The GNU stdc++ library (debugging files)
libstdc++2.10-dev - The GNU stdc++ library (development files)
libstdc++2.10-glibc2.2 - The GNU stdc++ library
libstdc++5-3.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++5-3.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++5-3.3-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.1-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.2-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-pic - The GNU Standard C++ Library v3 (shared library subset kit)

so looks libstdc++5 is there (see bolded line in your output).

don't know why apt-get refuses to install it. try going at it with synaptic, maybe it will figure it out. :)

---

