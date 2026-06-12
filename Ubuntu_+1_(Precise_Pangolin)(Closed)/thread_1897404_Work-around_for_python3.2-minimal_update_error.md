---
title: "Work-around for python3.2-minimal update error"
date: 2011-12-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2011-12-19
Most of you probably already know how to get around this sort of thing, but just in case:

```
paul@precise:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/python3.2-minimal_3.2.2-2ubuntu1_i386.deb
(Reading database ... 176233 files and directories currently installed.)
Preparing to replace python3.2-minimal 3.2.2-2 (using .../python3.2-minimal_3.2.2-2ubuntu1_i386.deb) ...
Unpacking replacement python3.2-minimal ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/bin/python3', which is also in package python3-minimal 3.2.2-0ubuntu2
Setting up python3.2-minimal (3.2.2-2ubuntu1) ...
Processing triggers for man-db ...
paul@precise:~$
```

---

### Post by Harry33 on 2011-12-19
There is already an update (3.2.2.-2ubuntu3) in the precise repos:
[https://launchpad.net/ubuntu/precise/+source/python3.2/3.2.2-2ubuntu3](https://launchpad.net/ubuntu/precise/+source/python3.2/3.2.2-2ubuntu3)

BTW
Could someone explain me why the package firefox depends on lsb-release,
which in turn depends on python 3, which in turn depends on python 3.2.
Precise is using python2.7 ATM, however.

---

### Post by paul_in_london on 2011-12-19
> **Harry33 said:**
> There is already an update (3.2.2.-2ubuntu3) in the precise repos:
[https://launchpad.net/ubuntu/precise/+source/python3.2/3.2.2-2ubuntu3](https://launchpad.net/ubuntu/precise/+source/python3.2/3.2.2-2ubuntu3)

BTW
Could someone explain me why the package firefox depends on lsb-release,
which in turn depends on python 3, which in turn depends on python 3.2.
Precise is using python2.7 ATM, however.

Hi Harry,

Yes there was no problem with the 3.2.2.-2ubuntu3 update, but that is a very strange chain of dependencies that you've listed and yet (as you point out):

```
paul@precise:~$ python --version
Python 2.7.2+
paul@precise:~$
``` :confused:

No packages are broken or held back at the moment though (at least for me anyway).

---

