---
title: "Freshly installed ubuntu 12.10 beta 2, and it wont start properly."
date: 2012-10-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by chrissy.millichamp on 2012-10-16
And I also have this error message executable path /usr/lib/upower/upowerd package upower 0.9.174. My unity menu nor my uper panel wont appear for some reason, it crashes, need help fast plz!

---

### Post by cariboo on 2012-10-17
We are way past the beta now, if you can get to a console, I'd suggest you update to the current version. At the prompt type the following command:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by chrissy.millichamp on 2012-10-17
Ok thanks, Im doing it right now as we speak, but it doesnt answer my question that why it freezes after login in, an nothhhing appears theres just my background and thats all....

---

### Post by cjcj on 2012-10-18
> **chrissy.millichamp said:**
> Ok thanks, Im doing it right now as we speak, but it doesnt answer my question that why it freezes after login in, an nothhhing appears theres just my background and thats all....

I am also getting this with a fully up to date QQ. It is working fine in gnome classic session (select that at the login screen). Although I have gnome shell installed, the gnome session just goes to gnome classic. (which is what I am working at the moment - really missing the dash etc.)

The Unity problem seems to stem from the fact that there is a bug with compiz at the moment so Unity cannot run until compiz is fixed. Someone is working on this, I believe, looking at the bug report in launchpad. I am running a modern nvidia graphics card (geforce 630.

I cannot explain why I can't get into gnome-shell though.

---

### Post by funicorn on 2012-10-18
If you can see the login window popping up and run into trouble after login, it's always helpful to check errors in ~/.xsession-errors.

---

### Post by cjcj on 2012-10-18
Delete .xsessions-errors, ctrl-bcksp, then tried to login to Unity session..

First few lines of .xsessions-errors file are ..

> gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session[18916]: WARNING: Session 'gnome-classic' runnable check failed: Child process exited with code 1

(gnome-panel:19010): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion `accelerator != NULL' failed

** (gnome-panel:19010): WARNING **: Unable to parse mouse modifier '(null)'

** Message: applet now removed from the notification area

(gnome-panel:19010): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion `accelerator != NULL' failed

** (gnome-panel:19010): WARNING **: Unable to parse mouse modifier '(null)'

** Message: using fallback from indicator to GtkStatusIcon
** Message: moving back from GtkStatusIcon to indicator

---- after that it has loads of seitgeist warnings that files I worked on yesterday cannot be found (slightly worrying but not the current problem. 

What is missing?

---

