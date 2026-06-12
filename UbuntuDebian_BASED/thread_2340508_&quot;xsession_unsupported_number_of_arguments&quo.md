---
title: "&quot;xsession unsupported number of arguments&quot;  after trying Wayland"
date: 2016-10-19
forum: Ubuntu/Debian BASED
---

### Post by neu5eeCh on 2016-10-19
Using KDE Neon, was curious to try Wayland. It barely worked so I uninstalled and returned to a Plasma session. 

Now,  when I boot up the system, I get a black screen with the error  message:  "xsession unsupported number of arguments (2) falling back to  default session".

If I click the okay button the error just keeps repeating itself. I can TTY but that's all. Any suggestions?

What I've tried:

1.) Checked .profile in home directory and compared to functioning system. Looks good.
2.) Checked .bashrc the same way. Looks good.
3.) Purged xorg and reinstalled.
4.) Purged SDDM and reinstalled.

Xsession error messages:

The X11 connection broke: I/O error (code 1)
X10 fatal IO error 4 (Interrupted system call) on X server ":0"
after 116 requests (116 known processed) with 0 events remaining.
Xsession: Xsession started for vtpoet at Tue Oct 18 [etc....]
Xsession: unspported number of arguments [etc....]

Also a couple lines later (with similar syntax: IO error 11

---

### Post by neu5eeCh on 2016-10-20
Solved. Reinstalled KDE Neon. Love the Ubuntu base and the fact that nothing is installed with Neon. Kind of like that. I can add only what I want and use.

---

