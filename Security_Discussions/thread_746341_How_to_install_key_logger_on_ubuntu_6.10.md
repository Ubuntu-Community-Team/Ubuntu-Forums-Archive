---
title: "How to install key logger on ubuntu 6.10"
date: 2008-04-05
forum: Security Discussions
---

### Post by daradib on 2008-04-05
Use the program LKL.

LKL is a userspace keylogger that runs under Linux on the x86 architecture. LKL sniffs and logs everything that passes through the hardware keyboard port (0x60). It translates keycodes to ASCII with a keymap file.

Enable the universe repository.
Install the package lkl (you can do so through the Synaptic Package Manager or via the command sudo apt-get install lkl).

You can probably find more information after you install the package by entering the commands man lkl OR lkl --help OR sudo lkl -h (the OR is to separate the commands; do the commands one at a time) in the terminal (Applications -> Terminal).

For more information see the threads [http://ubuntuforums.org/showthread.php?t=450806](http://ubuntuforums.org/showthread.php?t=450806) and [http://ubuntuforums.org/showthread.php?t=427829](http://ubuntuforums.org/showthread.php?t=427829)

Please don't hesitate to reply if you have any more questions. Cheers.

---

### Post by p_quarles on 2008-04-05
Moved to Security Discussions.

---

