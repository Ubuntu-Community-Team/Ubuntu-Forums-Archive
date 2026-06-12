---
title: "Everpad in 13.04"
date: 2013-01-22
forum: Ubuntu Development Version
---

### Post by AlanR8 on 2013-01-22
Evening all and a belated Happy New Year!

Had the Evernote app called Everpad happily installed in 12.04 and 12.10 but I can't get it to work in 13.04.

The PPA seems to have installed properly but:

> Unable to locate package everpad


I KNOW 13.04 is in development but does anyone else have the same issue or ideas how to resolve the issue?

TIA.

---

### Post by AlanR8 on 2013-01-23
24 hour Bump........:-)

---

### Post by mcduck on 2013-01-23
Most likely the PPA doesn't provide packages for 13.04 yet, as it's still so far from even being released...

---

### Post by sandyd on 2013-01-23
moved to raring

---

### Post by mc4man on 2013-01-23
packages for 13.04 have yet to be built, dep wait since 01/15
[https://launchpad.net/~nvbn-rm/+archive/ppa/+build/4219349](https://launchpad.net/~nvbn-rm/+archive/ppa/+build/4219349)
[https://launchpad.net/~nvbn-rm/+archive/ppa/+build/4219350](https://launchpad.net/~nvbn-rm/+archive/ppa/+build/4219350)

---

### Post by bmbaker on 2013-01-23
little trick change the name in the ppa from raring to quantal till its available ;-)

---

### Post by mc4man on 2013-01-23
> **bmbaker said:**
> little trick change the name in the ppa from raring to quantal till its available ;-)

In this case may prove slightly problematic as a couple of dependent libs aren't avail. in raring. 
If important to use now one could try installing the quantal versions of missing libs 
or
build the missing libs to /opt using  quantal sources  then link 
or
 build the whole mess to /opt with compatible to raring & each other sources & run everpad from /opt

---

