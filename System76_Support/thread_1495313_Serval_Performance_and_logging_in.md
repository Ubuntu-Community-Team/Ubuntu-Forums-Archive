---
title: "Serval Performance and logging in"
date: 2010-05-27
forum: System76 Support
---

### Post by RedRat on 2010-05-27
I just got my Serval Performance and quite happy with it, except for an exceptionally short battery life. I noticed today, that when I go to log in at start up, the login screen comes up twice. This has happened three times today. Each time I was very careful about typing my password. I would enter the password the first time and then the login screen would come back in and when I entered the password, the OS started normally.

This is Lucid Lynx.

Anyone else seen this odd behavior?

---

### Post by thomasaaron on 2010-05-28
I've not seen that at all, but it sounds like it might be related to this bug report...

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/178324](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/178324)

Try running this command from a terminal...

mv .gnome2 .gnome2.bk

Then reboot your computer.

Did that fix it?

---

### Post by RedRat on 2010-05-28
> **thomasaaron said:**
> I've not seen that at all, but it sounds like it might be related to this bug report...

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/178324](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/178324)

Try running this command from a terminal...

mv .gnome2 .gnome2.bk

Then reboot your computer.

Did that fix it?

Nope. Still coming up twice. ran the command as sudo.

---

