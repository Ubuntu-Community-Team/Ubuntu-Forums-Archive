---
title: "After restart, Ubuntu only shows wallpaper and cursor"
date: 2013-03-19
forum: Virtualisation
---

### Post by tzippy on 2013-03-19
I am running 10.04.3 on VMWare workstation. I had the vm running just fine but after restarting it I only get the wallpaper and a cursor.
I can switch to terminal (ctrl alt f2) and logon. But I do not get a desktop. I tried to restart gdm (**sudo /etc/init.d/gdm restart) **with no success.
Any help is appreciated! thanks!

EDIT: I noticed it's not the wallpaper but the login screen. But it's missing the user-selection-pane to login!

---

### Post by tzippy on 2013-03-19
This solved my problem: [http://ubuntuforums.org/showthread.php?t=1540558](http://ubuntuforums.org/showthread.php?t=1540558)
No idea why, but libz caused the problem.

---

