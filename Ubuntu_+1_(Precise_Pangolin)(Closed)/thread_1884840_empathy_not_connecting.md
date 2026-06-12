---
title: "empathy not connecting"
date: 2011-11-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bmbaker on 2011-11-22
empathy is failing to connect. anyone have this happening?

There was an error while trying to connect to the Telepathy Account Manager. The error was:

Process /usr/lib/telepathy/mission-control-5 received signal 5

---

### Post by effenberg0x0 on 2011-11-22
Empathy standard error messages are far from helpful. There are some tips on getting proper debug info in here: [http://telepathy.freedesktop.org/wiki/Debugging](http://telepathy.freedesktop.org/wiki/Debugging)

However, if you are running the latest update on PP, I will guess it's libglib update related. You might want to wait for the next update to its libs before proceeding to more hardcore tweaking and/or bug reporting.

---

### Post by MarjaE on 2012-01-26
Empathy's also stopped working for me, I have a Yahoo account, but only get a "Network Error" message. Obviously the network is working, since I'm typing here, but the "network error" has persisted despite quitting and restarting Empathy, logging out and logging back in, shutting down and rebooting, trying every debug suggestion I can find [some of which involve fields and checkboxes which no longer exist] and deleting and restoring that account.

---

