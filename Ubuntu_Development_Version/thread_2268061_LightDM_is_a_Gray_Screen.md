---
title: "LightDM is a Gray Screen"
date: 2015-03-05
forum: Ubuntu Development Version
---

### Post by Espionage724 on 2015-03-05
I installed Xubuntu 15.04 (today's (March 5th) daily) in BIOS-mode (full-disk encryption with LVM) and at the first boot after install, I'm shown a gray screen with a mouse cursor on it.

Doing a **sudo service lightdm start** just brings it back to that gray screen, so it seems the issue is with LightDM. I didn't have any issues from the Live environment; but I didn't do anything involving the login screen at all there (so maybe auto-logins are safe).

Doing a **sudo apt-get dist-upgrade** didn't fix it either.

**Edit**: Can get rid of the gray and login-in normally by just clicking once or twice, and the issue seems to go away entirely once I set-up multi-monitor properly.

---

### Post by dino99 on 2015-03-06
maybe try 'sudo dpkg-reconfigure lightdm'
or switch to gdm or xdm

---

### Post by ihoe3fze on 2015-03-08
[http://ubuntuforums.org/showthread.php?t=2267474&p=13237880#post13237880](http://ubuntuforums.org/showthread.php?t=2267474&p=13237880#post13237880)

---

### Post by Swimkido1 on 2015-08-06
Could you explain what you mean by setting up multi-monitor properly?  I am having the same problem with the gray screen, but want to see if that would fix the problem I am having.

Thank you.

---

