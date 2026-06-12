---
title: "Unable to disable gnome-keyring-daemon"
date: 2010-03-08
forum: Security
---

### Post by dc1 on 2010-03-08
I'm running Ubuntu 9.10.  

After removing the check mark next to "GNOME Keyring Daemon" in "Startup Applications Preferences" I reboot but the gnome-keyring-daemon runs anyway.  

dave@gobot:~$ ps -ef | grep key
dave      1339     1  0 09:55 ?        00:00:00 /usr/bin/gnome-keyring-daemon --daemonize --login


This is not really causing me any problems - I'm just reporting it since it looks like a bug.  Let me know if there's a more appropriate place to mention this.

---

