---
title: "fake updates?"
date: 2016-07-04
forum: Security
---

### Post by skywalker4 on 2016-07-04
hi there.
im using ubuntu 16.04 lts.
sometimes i notice updates on the ubuntu software center that software updater does not find, it is normal? thank you for your time. cheers

---

### Post by deadflowr on 2016-07-04
Yes, normal.

Ubuntu uses a mechanism called phased updates:
[https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")
Which is designed for the update manager (aka the software updater)

But the Gnome Software update system does not seem to honor that:
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1580833]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1580833")

(For the record though, only the update manager honors the phased updates mechanism, if you run updates through the command line, they too would get all the updates, just like the gnome software updates)

---

### Post by skywalker4 on 2016-07-04
thank you very much @deadflowr

---

