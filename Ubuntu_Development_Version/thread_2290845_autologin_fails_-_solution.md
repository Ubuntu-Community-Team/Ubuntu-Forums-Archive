---
title: "autologin fails - solution"
date: 2015-08-15
forum: Ubuntu Development Version
---

### Post by VMC on 2015-08-15
Xubuntu failed using autologin.
The fix is to remove the line "autologin-session=lightdm-autologin" from "/etc/lightdm/lightdm.conf, as that option has been unimplemented, per post#8 from this
[bug report]("https://bugs.launchpad.net/lightdm/+bug/1484083").

---

### Post by jerrylamos on 2015-08-16
Thanks - this is Wily Ubuntu Unity which has not been doing auto login since the last few updates despite settings.  
Commented out the line as you said.
Auto login now working again.

---

### Post by fjgaude on 2015-08-17
I wonder why that line was ever added to the .conf file?

---

### Post by VMC on 2015-08-17
> **fjgaude said:**
> I wonder why that line was ever added to the .conf file?

From the bug report post#8 "That option was previously unimplemented." It is implemented in Trusty, so no problem.
Apparently though, its ubiquity that's pulling it in.

---

