---
title: "nvidia-settings, nvidia-prime, missing python"
date: 2017-10-04
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-10-04
On new installs if installing nvidia drivers on a hybrid device one won't be able to open nvidia-settings nor run the prime-select command.
The reason is the python package has been removed from image though as currently constructed they need it.

Temp workaround is to install the python package, to run prime-select without installing python one would need to go
sudo python3 /usr/bin/prime-select intel or nvidia

[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1721394](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1721394)

---

### Post by mc4man on 2017-10-05
Solved because it never should have happened. Somehow on a 1 day old install python-minimal (python-2.7) was not installed.
Either the live session installer skipped it or nothing caused it to install..

Clearly seen when I installed the python dep package

> Commit Log for Wed Oct  4 17:19:48 2017


Installed the following packages:
libpython-stdlib (2.7.14-2ubuntu1)
python (2.7.14-2ubuntu1)
python-minimal (2.7.14-2ubuntu1)
python2.7 (2.7.14-2ubuntu2)
python2.7-minimal (2.7.14-2ubuntu2)

Everything but the python package should have already been installled,

---

### Post by mc4man on 2017-10-05
So not actually solved.
I was under incorrect assumption that if packages were on the image manifest they would be installed. Apparently that's not the case, at least with python-minimal, python2.7, ect.

---

