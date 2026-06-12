---
title: "something's wrong with Trusty's logo"
date: 2014-04-19
forum: Ubuntu, Linux and OS Chat
---

### Post by mariceles on 2014-04-19
I have a problem with the logo in settings, it says 13.10 instead of 14.04! This is a fresh install.


[http://s27.postimg.org/x4xs00t6q/2014_04_19_22_16_25.jpg](http://s27.postimg.org/x4xs00t6q/2014_04_19_22_16_25.jpg)

*edit: How do I report this bug?

---

### Post by bapoumba on 2014-04-19
The img was not displayed properly, I changed it to its direct url.

---

### Post by buzzingrobot on 2014-04-19
Did you upgrade from 13.10 or do a fresh install?

Just to make sure you are running 14.04, open a terminal and enter and run```
cat /etc/issue
``` That will display a one-line file that should say ```
Ubuntu 14.04 LTS \n \l

```

During development of 14.04, some components displayed "13.10" until relatively late when new art became available.  If, by chance, you downloaded and used an old 14.04 install image, then that might account for it. (If so, here's the link for 14.04: [http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/).

(To open a terminal, tap the Super/Windows key and begin typing "Terminal", then click on the icon when it appears.)

(Bug reporting docs: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs).  You'll need a Launchpad account: [https://help.launchpad.net/YourAccount/NewAccount](https://help.launchpad.net/YourAccount/NewAccount).)

---

### Post by grahammechanical on 2014-04-19
Are you using Ubuntu or Ubuntu Gnome? If it is Ubuntu Gnome then someone else reported that issue a day ago. It is an oversight.

Regards.

---

### Post by cariboo on 2014-04-20
Check the Ubuntu Gnome release notes for known issues available [here]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/UbuntuGNOME").

---

