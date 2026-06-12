---
title: "Ubuntu 7.04 Problem"
date: 2008-01-18
forum: System76 Support
---

### Post by KevMeistr on 2008-01-18
Hey Everyone who visits this post

Here's the problem.....

I was busy adding a printer from a network when suddenly the electricity went off...when I switch back on, I find that apt-get isn't installed and so I cannot get to the log in screen.

Anyway I can get into the Desktop without re-installing linux.   :popcorn:

---

### Post by thomasaaron on 2008-01-18
I don't think apt-get has anything to do with whether or not you get to the login screen. apt is a utility for managing software (downloads and such).

Do you get to the screen where it says something like "Grub...3..2..1..."?
If you do, you can hit the escape key and then select the recovery mode kernel.
This will bring you to a command prompt from which you can try to recover your system.

You might also try to run from a live cd, mount your home partition and try to figure out what is wrong with it.
At a bare minimum, maybe you can do this to recover any important data before re-imaging the computer.

---

