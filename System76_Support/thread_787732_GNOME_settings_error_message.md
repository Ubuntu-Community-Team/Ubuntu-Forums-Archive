---
title: "GNOME settings error message"
date: 2008-05-09
forum: System76 Support
---

### Post by ewg on 2008-05-09
System 76 Sable
Ubuntu 8.04  32 bit

I've been getting the following message at startup frequently. Any idea what the cause is?

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

---

### Post by thomasaaron on 2008-05-09
That is a dbus bug. See...
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)

There are number of theories on it:
1. Ubuntu is tripping over its own feet during startup and running certain programs before they should be run, which causes conflicts... blah blah blah...

2. There is a missing dependency: The dbus-x11 package. This one looks the most promising to me. To try it out, go to a teminal and run this command...
> 
sudo apt-get --reinstall install dbus-x11

There is a work-around here that involves modifying a script...
[https://bugs.edge.launchpad.net/ubuntu/+source/gconf2/+bug/139368](https://bugs.edge.launchpad.net/ubuntu/+source/gconf2/+bug/139368)
...to keep dbus from tripping over itself. If the above fix doesn't work, we can try that.

---

### Post by ewg on 2008-05-09
Thanks. I've had a few start ups with no problems after the last round of updates. I'll run your suggestion when (if) it happens again.

EWG

---

