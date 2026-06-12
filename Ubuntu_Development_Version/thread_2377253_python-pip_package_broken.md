---
title: "python-pip package broken"
date: 2017-11-11
forum: Ubuntu Development Version
---

### Post by monkeybrain20122 on 2017-11-11
See this thread here. same with 18.04
[https://ubuntuforums.org/showthread.php?t=2376477](https://ubuntuforums.org/showthread.php?t=2376477)

Basically pip install fails for all packages for slow internet connection . When internet is slow, pip has a way to retry download but some Debian/Ubuntu modification has screwed it up.
[https://github.com/pypa/pip/issues/3943](https://github.com/pypa/pip/issues/3943)
[https://github.com/pypa/pip/issues/4779](https://github.com/pypa/pip/issues/4779)
[https://github.com/pypa/pip/issues/4847](https://github.com/pypa/pip/issues/4847)

Removing python-pip and install from [upstream]("https://pip.pypa.io/en/stable/installing/") then everything works

Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/python-pip/+bug/1586859")

---

