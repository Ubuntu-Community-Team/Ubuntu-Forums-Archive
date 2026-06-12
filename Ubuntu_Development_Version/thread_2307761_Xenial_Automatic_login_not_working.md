---
title: "Xenial: Automatic login not working"
date: 2015-12-28
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-12-28
I'm having a hard time dealing with automatic login?  I set it to auto during installation and it didn't work.  I set it in the settings menu (user) and try a few command lines.  I'm still getting the pop-up asking for the password (startup, restart, lock screen).  Anyone can help?

---

### Post by dino99 on 2015-12-28
maybe your profile is damaged; try with a new user. Or reconfigure lightdm, or switch to gdm/....

---

### Post by MikeMecanic on 2015-12-28
> **dino99 said:**
> maybe your profile is damaged; try with a new user. Or reconfigure lightdm, or switch to gdm/....

In deed my profile was damaged.  Was not able to create a second user and switch to lightdm.  It was ok for startup and reboot but not logout and lock screen. Prefer Gnome  default set up.  Made a fresh install with today"s build and have the same issue.  Did not try anything yet.

---

### Post by fthx on 2015-12-29
I've got the same issue with a fresh install (Ubuntu Gnome) on an old computer.
If I remember right what I've done in the past, I manually added my user to
```
nopasswdlogin:x:123:
```
in
```
 /etc/group
```

---

