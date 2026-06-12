---
title: "Re: python2.7"
date: 2020-01-30
forum: Ubuntu Development Version
---

### Post by mc4man on 2020-01-30
As part of the process to remove python2.7 some packages are no longer built though python2.7, python2-minimal, ect,  are. 
It's received a symlink of python2, the previous symlink of python is no longer provided. 
Whether there is any future move to use the command of python for python3, no idea, a bug report on this doesn't indicate so..
(- and there is a refusal to add back python symlink though it's only a 1 line edit to python2-minimal source.

For the few that still use python2.7, if it's an editable text file one could simply change the shebang to python2.
However there are cases where  editing isn't possible so here a simple restore of the symlink.
```
sudo ln -sf '/usr/bin/python2' /usr/bin/python
```
ex.
```
$ file /usr/bin/python /usr/bin/python2
/usr/bin/python:  symbolic link to /usr/bin/python2
/usr/bin/python2: symbolic link to python2.7
```

Edit: any packages that dep on python need to change to python2-minimal & edit ant shebangs, if any, to python2

---

### Post by mc4man on 2020-04-18
There is a new package available that returns python symlink
python-is-python2

---

### Post by Doug S on 2020-04-18
> **mc4man said:**
> There is a new package available that returns python symlink
python-is-python2Yes, python-is-python3 does also, but it doesn't provide the python package, on purpose.
Please see [bug report here]("https://bugs.launchpad.net/ubuntu/+source/what-is-python/+bug/1868444").

---

### Post by mc4man on 2020-04-18
Well I'd have no use to link  python3 to python here, maybe some would, don't know why though.

At least they returned symlink and provides , orig. bug report I had was summarily dismissed as too bad, change shebangs, don't care otherwise..

---

### Post by Doug S on 2020-04-19
> **mc4man said:**
> Well I'd have no use to link python3 to python here, maybe some would, don't know why though.I have 2 use cases, both from the kernel source tree. The challenge being that they must work on all distributions, not just Ubuntu.

1.) tools/power/x86/intel_pstate_tracer/intel_pstate_tracer.py

The script has been tested on both python 2.7 and python 3, and I simply want it to work, without having to pull in any python 2 stuff.
I maintain this script, and can change the shebang if required.

2.) linux/scripts/diffconfig

I use this one all the time, but have not yet looked into why it doesn't work. Maybe it is just the shebang, I don't know.

Note that there a bunch of other scripts in the source tree that will have issues, but myself, I only use the above 2.

All the references and discussions I have found do NOT have any consistent advise for the shebang. It seems to be some argument between linux factions. [One reference]("https://blogs.gnome.org/mcatanzaro/2018/02/16/on-python-shebangs/").

---

