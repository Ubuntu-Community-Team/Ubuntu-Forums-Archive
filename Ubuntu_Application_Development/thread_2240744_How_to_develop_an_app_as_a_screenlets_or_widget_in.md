---
title: "How to develop an app as a screenlets or widget in tray?"
date: 2014-08-22
forum: Ubuntu Application Development
---

### Post by ppn029012 on 2014-08-22
I would like to write a small app for monitoring my server, for seeing which script is running, starting scripts, stop it or restart it, as a small screenlets or widget in the tray.

Is there any resources I can start with? It seems that the screenlets [ [http://screenlets.org](http://screenlets.org) ] fits my goal, but it seems to be closed.


Thanks in advance,
Yunong

---

### Post by ian-weisser on 2014-08-22
[http://developer.ubuntu.com](http://developer.ubuntu.com) has many resources.

All interaction with system indicators and notification is done using dbus. So you'll need to learn how to use dbus in your favorite language.

It also depends which flavor of Ubuntu you are using. Unity, for example, uses AppIndicators instead of a System Tray. Very different usage and capabilities, but doing the same thing.

---

### Post by ppn029012 on 2014-08-23
Thanks for your great guide!

---

