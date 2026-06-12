---
title: "double entries in applications"
date: 2014-03-02
forum: Ubuntu Development Version
---

### Post by d-cosner on 2014-03-02
I noticed I have two icons for privacy settings and sound in the applications lens. Anyone else have this?

---

### Post by nomenkultur on 2014-03-02
had the same problem 2 weeks ago, the latest images took care of that bug and now you only get double entries in the list to choose an 'application to launch with'

---

### Post by d-cosner on 2014-03-02
I just did a dist upgrade and found the double entries.

---

### Post by mc4man on 2014-03-02
If you're** just running Unity** then remove gnome-control-center, gnome-control-center-data & gnome-settings-daemon
The 2nd  sound  icon is  from gnome-control-center-data, there are 2 security ones in /usr/share/applications but only one will show once gnome-settings-daemon is removed, the dupe is worthless anyway  (gnome-activity-log-manager-panel.desktop

Do make sure you have unity-settings-daemon & unity-control-center installed

---

### Post by d-cosner on 2014-03-02
Thanks mc4man! That took care of the double entries. I had to log out and back on to get rid of the extra privacy settings icon but everything looks good now. Thanks again!

---

