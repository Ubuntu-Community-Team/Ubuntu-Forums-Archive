---
title: "Kubuntu Plasma 5"
date: 2014-07-10
forum: Ubuntu Development Version
---

### Post by Hazzabin on 2014-07-10
While installing the new Plasma 5 for testing, the 'powerdevil' is trying to "overwrite", how do I fix this issue

"[COLOR=#000000][FONT=Ubuntu]E: /var/cache/apt/archives/powerdevil_4%3a4.98.0-0ubuntu1~ubuntu14.10~ppa3_amd64.deb: trying to overwrite '/etc/dbus-1/system.d/org.kde.powerdevil.backlighthelper.conf', which is also in package kde-workspace-data 4:4.11.10-0ubuntu5

any help gratefully appreciated[/FONT][/COLOR]

---

### Post by JMB74 on 2014-07-11
From what I understand the packages in the PPA or that will eventually be uploaded to the main archive are meant to replace the existing KDE 4 ones, so there should be breaks and replaces to prevent a conflick like that with the old packages.

So can report to the kubuntu team as a packaging bug.

In the meantime you could remove the offending old [COLOR=#000000][FONT=Ubuntu]kde-workspace-data [/FONT][/COLOR] package. May with dependencies on it take a fair part of your KDE4 with it, but it's going anyway, so no big deal.

Then you should be able to upgrade, making sure after doing that that all the required new packages for KF5 and plasma 2 got pulled in, and manually installing any that got missed via a package manager.

---

### Post by Hazzabin on 2014-07-11
Many thanks for your reply JMB74

Yep seems to be a few issues there, maybe I'll hang off and not be so impatient :)

or I keep playing and drive myself nuts  :(

---

### Post by buzzingrobot on 2014-07-12
I came across the same problem yesterday using the kubuntu-ppa/next PPA on a 14.10 Kubuntu install. Tried various incantations I found to deal with that powerdevil overwrite issue, unsuccessfully.  I suspect it's too early to expect things to go smoothly. (In particular, I installed sddm, which then failed to appear on a reboot.  "dpkg-reconfigure sddm" didn't display the expected choice of display managers.)

You can check the current status of package builds here: [http://qa.kubuntu.co.uk/kf5-status/build_status_5.0.0_utopic.html](http://qa.kubuntu.co.uk/kf5-status/build_status_5.0.0_utopic.html).

I saw a mention on the Kubuntu devs list of a plan to release a separate installable ISO based on Plasma 5 and Framework 5 once they're released.  Don't know how firm that plan is, however.

---

### Post by Hazzabin on 2014-07-12
thanks for that info buzzingrobot

---

