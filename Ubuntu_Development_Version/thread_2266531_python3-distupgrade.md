---
title: "python3-distupgrade"
date: 2015-02-23
forum: Ubuntu Development Version
---

### Post by zika on 2015-02-23
```
Setting up python3-distupgrade (1:15.04.8) ...  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeViewKDE.py", line 37
    from PyQt5.QtGui import QTextOption, QPixmap, QIcon,
                               ^
SyntaxError: trailing comma not allowed without surrounding parentheses
dpkg: error processing package python3-distupgrade (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:15.04.8); however:
  Package python3-distupgrade is not configured yet.


dpkg: error processing package ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on ubuntu-release-upgrader-core (= 1:15.04.8); however:
  Package ubuntu-release-upgrader-core is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-distupgrade (= 1:15.04.8); however:
  Package python3-distupgrade is not configured yet.


dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
Processing triggers for menu (2.1.47ubuntu1) ...
Errors were encountered while processing:
 python3-distupgrade
 ubuntu-release-upgrader-core
 ubuntu-release-upgrader-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Remove offending trailing comma and apply```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up python3-distupgrade (1:15.04.8) ...
Setting up ubuntu-release-upgrader-core (1:15.04.8) ...
Setting up ubuntu-release-upgrader-gtk (1:15.04.8) ...
```

---

