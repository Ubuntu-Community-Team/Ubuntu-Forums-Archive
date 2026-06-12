---
title: "Opening Priveledged Programs from User Desktop"
date: 2010-04-13
forum: Security
---

### Post by quiryn88 on 2010-04-13
How do you open a program, in this instance "Zenmap", from the desktop in a user account when it requires root privileges? Is there a way to be prompted for the password, the same way, for instance, you're prompted when mounting a new file system or making a change to the system? I tried entering 'sudo /usr/bin/zenmap' when creating the shortcut, however that didn't work. Any help would be appreciated.

---

### Post by cariboo on 2010-04-13
Use gksudo instead of sudo. Sudo only works if your are opening a program in a terminal.

---

### Post by Jive Turkey on 2010-04-14
you might find it helpful to edit the menu entry for that application with System > Preferences > Main Menu

select Zenmap, click properties and put "gksu" in front of the command.  It will prompt you for the passoword in order to start it from the menu after that.

---

### Post by gradinaruvasile on 2010-04-14
If you want to launch from the GUI, press alt+f2 and type in the program name you want. And if you want it with root rights, append gksudo in front of it.
Example:

gksudo nautilus

---

