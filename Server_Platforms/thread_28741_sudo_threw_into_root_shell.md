---
title: "sudo threw into root shell"
date: 2005-04-21
forum: Server Platforms
---

### Post by m1thrand1r on 2005-04-21
I had a problem with xfree so I edited the /etc/X11/XFREE-4 file by issuing a sudo command to use vim, after editing the file I issued startx and everything ran fine.  After that I used log out within gnome and instead of giving me the option to reboot or whatever it took me straight into a root shell.  What's going on with this?

---

### Post by XDevHald on 2005-04-21
Does that too me sometimes as well, nothing really to be worried about, but if it does concern you, just startx again and it'll take you to the normal login screen, select your session, and choose "Gnome" this will take you back to your customed. display desktop.

---

### Post by fdoving on 2005-04-21
[QUOTE=m1thrand1r]I had a problem with xfree so I edited the /etc/X11/XFREE-4 file by issuing a sudo command to use vim, after editing the file I issued startx and everything ran fine.  After that I used log out within gnome and instead of giving me the option to reboot or whatever it took me straight into a root shell.  What's going on with this?[/QUOTE]
 When you start X manually with 'startx' you're already logged in, and you start X like every other application you start from the commandline. When you exit the program/X you return to the shell. That's normal, and that's what most people expect happens.

If you start X with a display manager, like GDM or KDM you get to choose what to do on logout.

the command for restarting GDM is: 'sudo invoke-rc.d gdm restart'

- Frode

---

### Post by m1thrand1r on 2005-04-22
My problem was not with being taken back to the shell but the fact that i first issued startx as a normal user and then was thrown into a full ROOT shell.  I'd say that is quite a serious security problem.

---

### Post by nautilus on 2005-04-22
are you suuuure that was the same shell?

you may have been logged in as root on another vt.

---

