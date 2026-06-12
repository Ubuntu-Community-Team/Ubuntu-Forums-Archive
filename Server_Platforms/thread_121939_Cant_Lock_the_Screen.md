---
title: "Cant Lock the Screen"
date: 2006-01-26
forum: Server Platforms
---

### Post by intellidenuser on 2006-01-26
Hey,

I have Ubuntu loaded onto a laptop and it needs to be locked (dont want users walking up to it and messing with stuff). Also, I need to be able to VNC to the box. VNC is active but, if Ubuntu is logged out, it wont allow VNC (a known issue). So the alternative is to lock the screen, right? When I go to System-> lock screen, nothing happens. What's the deal?

---

### Post by bernardfrancois on 2006-01-28
I think you can set your screensaver to ask a password before returning to your desktop.

If you set that, it will lock your laptop automatically when youre away after some time (positive is that you don't have to remember to lock it).

If you still want to lock your computer manually, you can tell the xscreensaver process to start the screensaver, or maybe even to lock the screen without that option being set for every time the screensaver starts.

Read the output of **man xscreensaver-command** for more information.

If you found out which command to use to lock the screen, you can add a shortcut to that command in your gnome menu.

Also, please post the command to lock the screen using xscreensaver if you found it, I'm curious about it (but since I don't really need it and I have an exam within two days I won't take the time to find it out myself) - and it might also help other users.

---

### Post by intellidenuser on 2006-01-31
Ok, enabled the screensaver and enabled "lock the screen". It does that. But now, VNC doesn't work again? Anyone have a solution to this?    :confused:

---

### Post by bernardfrancois on 2006-01-31
I guess you'd better start another topic for that, so people with more experience with VPN can reply on it...

---

### Post by intellidenuser on 2006-02-01
Ok, moved to following location:

[http://ubuntuforums.org/showthread.php?p=698131#post698131](http://ubuntuforums.org/showthread.php?p=698131#post698131)

---

