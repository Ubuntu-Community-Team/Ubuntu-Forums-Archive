---
title: "How to reopen terminal?"
date: 2010-08-11
forum: Server Platforms
---

### Post by Caskast on 2010-08-11
Hey guys, i accidently closed the terminal on a fresh ubuntu server install, all i have is a grey screen (no desktop) how do i re-open the terminal so i can carry on working -_-

---

### Post by Slim Backwater on 2010-08-11
Sounds like you are running X without a window manager.  Try rightclicking the desktop for a menu, or even pressing CTRL+ALT+BACKSPACE to kill X.

I'd probably CTRL+ALT+F1 to dump to a text console, "export DISPLAY=:0.0" and run "xterm &" and then CTRL+ALT+F7 to go back to X.

---

### Post by Caskast on 2010-08-11
When i try these keybinds, they only work on my local computer, not through VNC Viewer, i managed to get the terminal backup by rebooting the remote server, but i believe a desktop was not requested on purchase because we don't need any graphical GUI

---

