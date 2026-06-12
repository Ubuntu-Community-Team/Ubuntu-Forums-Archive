---
title: "No Desktop after Mar 24 update"
date: 2014-03-24
forum: Ubuntu Development Version
---

### Post by makitso on 2014-03-24
Well,well, did todays large update, new . 19 kernel, etc. and after a reboot no desktop.  I have the gnome shell installed on Ubuntu.  However, there is no unity shell either.  I get the login screen with background.  Put in my pw and bong, nothing happens.  Just the login display and an active mouse.  Tried the.18 kernel and same.

So, did the same update on my laptop.  One thing was different, the laptop update asked me a bunch of keep/replace questions, whereas the broken one did not.

.xsession-errors had Init: dbus pre-start process (2187) terminated with status 2.

---

### Post by deadflowr on 2014-03-24
This seems to have occured to a few users.
The package ubuntu-session was probaly not installed.
That should at least get you unity.
Don't know about the gnome-shell problem.
Here's a related bug report
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826)
and another poster in a different thread about this
[http://ubuntuforums.org/showthread.php?t=2209080&page=9&p=12957487#post12957487](http://ubuntuforums.org/showthread.php?t=2209080&page=9&p=12957487#post12957487)

---

### Post by makitso on 2014-03-24
Nope, I have both gnome.desktop and ubuntu.desktop in xsessions.

If I run sudo gdm I get Maximum of X display failurs reached: check X server log for errors.

---

### Post by deadflowr on 2014-03-24
Does the password take or does it simply blank out, or something like that?
I mean does the password field fill in when typing.

---

### Post by makitso on 2014-03-24
I typed in the wrong pw and it complained.  Typing in the right pw and the block disappears and then there is nothing e.g. the background background is showing and the mouse is active.

---

