---
title: "Software Center won't start"
date: 2012-01-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Sportsstar99 on 2012-01-21
When trying to start software center in ubuntu 12.04 daily build i get this error 
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
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 32, in <module>
    from bsddb import db as bdb
  File "/usr/lib/python2.7/bsddb/__init__.py", line 67, in <module>
    import _bsddb
ImportError: No module named _bsddb
```I tried reinstalling python bt i still get the same error and help?

---

### Post by Double.J on 2012-01-21
Hi there, Welcome to the forums!

Have you installed all the latest updates and restarted? (I've picked up 151 in the last 48 hours)

12.04 bugs are reported [here]("http://ubuntuforums.org/showthread.php?t=1888420")

And the general area of the forums is [+1]("http://ubuntuforums.org/forumdisplay.php?f=412")

At the moment we're moving so fast towards the Alpha 2 milestone that things are breaking and being fixed on a daily basis... I'd be inclined to use synaptic for a day or two and if the same fault isn't resolved file a bug report  :)

---

### Post by oldos2er on 2012-01-21
Thread moved to Ubuntu +1 (Precise Pangolin)

---

### Post by grahammechanical on 2012-01-21
How long ago did this happen? Very early on 19th this happened to me. I got the Software Centre closed unexpectedly message before the user interface had a chance to appear. Then Software Centre would not load. The icon in the Launched just wiggled.

I use synaptic to re-install and that did not work. Then just now I tried to open the Software Centre and it is working!

I had earlier run an update which included some Python stuff if I remember. so, that may be the answer. Run Update Manager.

A lot of issues can be fixed by waiting a bit. It is also good to reports bugs.

Regards.

---

### Post by effenberg0x0 on 2012-01-21
Confirmed, on a fresh install of the latest daily ISO 64-Bit.
Adding python-bsddb3 or python3-bsddb3 won't fix it.
Downgrading is proposed at: [https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/440889](https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/440889) and dups.

An (old) patch is provided [here]("http://marc-abramowitz.com/archives/2007/11/28/hacking-os-xs-python-dbhash-and-bsddb-modules-to-work/"), but it does not work for me. 
```

 --- dbhash.py.orig      2007-11-28 10:16:33.000000000 -0800 
+++** dbhash.py**   2007-11-28 10:36:52.000000000 -0800 
@@ -2,7 +2,7 @@   
import sys  
try: 
-    import bsddb 
**+    import bsddb3 as bsddb  **
except ImportError:      # prevent a second import of this module from spuriously succeeding      del sys.modules[__name__] 

```

---

### Post by mc4man on 2012-01-22
Comes from the recent *python2.7* upgrades, there were 4 this week. So should be fixed shortly with either a python update or SC

fixed w/ python2.7 2.7.2-13ubuntu4

---

### Post by jbicha on 2012-01-22
By the way, if you use webkit 1.7.4 from either the GNOME3 or the ubuntu-desktop PPAs,  software-center won't work.

---

### Post by GeorgeVita on 2012-01-22
Recent installation from daily live (22-Jan) plus updates, 32 bit, Unity, Ubuntu Software Center works fine.
G

---

### Post by ronacc on 2012-01-22
AMD64 install here , fully updated , running Gnome-Shell . USC working ok .

---

### Post by effenberg0x0 on 2012-01-22
I had made some changes to Python 2.7 to allow the previous state of Software Center to run, so sudo apt-get install --reinstall python2.7 was needed in my case, to drop my changes and return it to defaults. Just a note as some may have taken the opportunity to mess with python bsddb too.

---

