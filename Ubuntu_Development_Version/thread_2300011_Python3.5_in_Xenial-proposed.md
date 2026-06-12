---
title: "Python3.5 in Xenial-proposed"
date: 2015-10-23
forum: Ubuntu Development Version
---

### Post by harry332 on 2015-10-23
The python3.5 is now uploaded into proposed repos.
(If you want to be careful, and bla bla, you do not enable proposed ...)
However this means a new python anyway.

I wonder when the python2.7 is dropped for good.
It seems that only libpeas is one important package to depend on python2.7.

---

### Post by ventrical on 2015-10-23
> **harry332 said:**
> The python3.5 is now uploaded into proposed repos.
(If you want to be careful, and bla bla, you do not enable proposed ...)
However this means a new python anyway.

I wonder when the python2.7 is dropped for good.
It seems that only libpeas is one important package to depend on python2.7.

I got the xorg-n-n package and I'll bet that will bust your system. So I didn't upgrade it.

edit:
Did not bus system.

```

ventrical@ventrical-OptiPlex-755:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
ventrical@ventrical-OptiPlex-755:~$ 

```

---

### Post by mc4man on 2015-10-23
> **harry332 said:**
> 

I wonder when the python2.7 is dropped for good.
It seems that only libpeas is one important package to depend on python2.7.
No time soon, certainly not for 16.04
(much more than libpeas uses 2.7

---

### Post by oldfred on 2015-10-23
Ubuntu and other distributions have been saying for a long time that the next version will be python 3 only, but python 2.7 would still be available. I thought they said it again for 16.04, but maybe it was 16.10?

 Shipping only Python 3 on the 12.10 CD
[https://wiki.ubuntu.com/Python/FoundationsQPythonVersions](https://wiki.ubuntu.com/Python/FoundationsQPythonVersions)

---

### Post by dino99 on 2015-10-23
This is the main job actually done for the concerned packages on xenial

"  No-change rebuild for python3 defaults change.

 -- Matthias Klose  "

---

### Post by anca-emanuel on 2015-10-23
There is an transition tracker
[http://people.canonical.com/~ubuntu-archive/transitions/html/onlypy3oncd.html](http://people.canonical.com/~ubuntu-archive/transitions/html/onlypy3oncd.html)
For python 3.5 as default [http://people.canonical.com/~ubuntu-archive/transitions/html/python3.5.html](http://people.canonical.com/~ubuntu-archive/transitions/html/python3.5.html)

Debian: [https://wiki.debian.org/Python/StretchRoadmap](https://wiki.debian.org/Python/StretchRoadmap)
[https://release.debian.org/transitions/html/python3.5.html](https://release.debian.org/transitions/html/python3.5.html)
And there will be another transition to 3.5 as default.
Next step, eliminate 3.4
And some time in the future, eliminate any dependency to 2.7

---

### Post by rrnbtter on 2015-10-23
Greetings,
I am updating with proposed enabled but still have v2.7.
Probably being held back for dependencies.

rrnbtter@rrnbtter-Satellite-L305:~$ apt-cache policy python
python:
  Installed: 2.7.9-1
  Candidate: 2.7.9-1
  Version table:
 *** 2.7.9-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial/main i386 Packages
        100 /var/lib/dpkg/status
rrnbtter@rrnbtter-Satellite-L305:~$

---

