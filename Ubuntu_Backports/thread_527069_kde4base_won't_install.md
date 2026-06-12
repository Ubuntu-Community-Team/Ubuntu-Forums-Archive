---
title: "kde4base won't install"
date: 2007-08-16
forum: Ubuntu Backports
---

### Post by jej2003 on 2007-08-16
I am trying to install kde4base and am getting the following error
```
 sudo apt-get install kde4base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde4base: Depends: kdelibs5 but it is not going to be installed
            Depends: kdepimlibs5 but it is not going to be installed
E: Broken packages

```
if I attempt to just install kdelibs5 I get
```
sudo apt-get install kdelibs5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs5: Depends: dbus-x11 but it is not installable
E: Broken packages

```
can someone explain to me what's goign on?

---

