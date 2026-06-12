---
title: "Software Center Issues"
date: 2011-11-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by go7Ul1ai on 2011-11-08
Is anyone else having trouble opening up the Software Center?

Here's the terminal output:

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 131, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 82, in <module>
    from softwarecenter.ui.gtk3.panes.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/installedpane.py", line 36, in <module>
    from softwarecenter.ui.gtk3.models.appstore2 import (
  File "/usr/share/software-center/softwarecenter/ui/gtk3/models/appstore2.py", line 33, in <module>
    from softwarecenter.backend.reviews import get_review_loader
ImportError: No module named reviews

```

---

### Post by philinux on 2011-11-08
Yes is does not start from the launcher. But this is very early days into the cycle.

---

### Post by P-I H on 2011-11-08
I installed the daily build from 07 November today. Direct after installation I used Software Center to install Synaptic, but after the installation of Synaptic it did not start.

---

### Post by ventrical on 2011-11-08
Works beautiful here.

---

### Post by mc4man on 2011-11-08
should be a new package available soon if not already
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/887392](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/887392)

---

### Post by ventrical on 2011-11-08
Whoopps ! Just updated!! Does not work so beautiful here :(

---

### Post by ventrical on 2011-11-08
> **mc4man said:**
> should be a new package available soon if not already
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/887392](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/887392)


it reports that the fix is released but it is not in the repos.

assumedly so.

---

### Post by mc4man on 2011-11-08
> **ventrical said:**
> it reports that the fix is released but it is not in the repos.

assumedly so.

So be there soon, at least in main server (on 11.10 atm
The package is built as seen here
[https://launchpad.net/ubuntu/+source/software-center/5.1.1.1/+build/2910750](https://launchpad.net/ubuntu/+source/software-center/5.1.1.1/+build/2910750)

---

### Post by philinux on 2011-11-08
> **ventrical said:**
> Whoopps ! Just updated!! Does not work so beautiful here :(

Aha. Got you too then. Testing ain't half fine eh. ;)

---

### Post by ventrical on 2011-11-08
> **philinux said:**
> Aha. Got you too then. Testing ain't half fine eh. ;)

@philinux, mac4man,

Yes suh! Thar she blows !

:)

---

### Post by P-I H on 2011-11-09
Works fine now. There is also a new feature "Add to Launcher".

---

