---
title: "Ubuntu 16.04 LTS Shows Python 2.7"
date: 2016-07-04
forum: Server Platforms
---

### Post by ptmuldoon on 2016-07-04
I just completed fresh install of Ubuntu Server 16.04 LTS on Virtual Machine.  And then ran update and upgrade of all packages.  But it appears Python 2.7 is installed although I believe Ubuntu 16.04 is suppose to come with Python 3.5.1?

Can anyone possibly confirm that and/or tell how to upgrade to the latest Python?

```

ptmuldoon@HomeAssistant:~$ lsb_release
No LSB modules are available.
ptmuldoon@HomeAssistant:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04 LTS
Release:        16.04
Codename:       xenial
ptmuldoon@HomeAssistant:~$ python
Python 2.7.11+ (default, Apr 17 2016, 14:00:29)
[GCC 5.3.1 20160413] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

```

---

### Post by &amp;KyT$0P# on 2016-07-04
What happens if you type "python3" instead of "python" at the command line?

---

### Post by ptmuldoon on 2016-07-04
> **halogen2 said:**
> What happens if you type "python3" instead of "python" at the command line?

Thank you that :)

I no expert at linux stuff, and just learned that yes, both python2 and python3 appear to be installed.  So running python3 showed me 3.5.1 is installed as well.

---

