---
title: "KDE 4 rc1"
date: 2007-11-24
forum: Repositories &amp; Backports
---

### Post by travken on 2007-11-24
travkin@delta:/etc/apt$ sudo apt-get -f install kdebase-dev-kde4 kdebase-workspace-dev kdebase-runtime
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-dev-kde4: Depends: kdepimlibs5-dev (>= 3.96.0) but it is not going to be installed
                    Depends: libsmbclient-dev but it is not going to be installed
  kdebase-workspace-dev: Depends: kdepimlibs5-dev (>= 3.96.0) but it is not going to be installed
                         Depends: libstrigiqtdbusclient-dev (>= 0.5.7) but it is not going to be installed
E: Broken packages
travkin@delta:/etc/apt$                      

how to fix?

---

### Post by ElTimo on 2007-11-24
I'm not sure if this will help, but I also had a problem installing KDE 4 rc1 and i found that uninstalling any packages that you may have installed previously that deal with kde 4 (basically, uninstall kdelibs5) helped ease my problems. I have Plasma running, but I can't seem to get the panel or the rest of the desktop to work...but I'll save that for another post ;-). Hope this helps!

-ElTimo

---

