---
title: "Problems booting 7.10"
date: 2008-01-05
forum: Server Platforms
---

### Post by Ooder on 2008-01-05
Hello,
I recently installed Ubuntu 7.10 Server 64 bit on my machine.  The installation when normal as usual, and everything was working perfectly.  I then installed Ubuntu Desktop (sudo apt-get install ubuntu-desktop) because I like to use a GUI sometimes.

Since I normally don't use the GUI, and a lot of the features I don't need, I uninstalled (sudo apt-get remove gdm) gdm to it would boot to the terminal instead into the desktop.  This also removed ubuntu-desktop and its extra features.  I then did a startx and it went into the the desktop perfectly.

This is where the problem occurred.  Now, when I reboot the computer, I get passed the GRUB menu, and the monitor goes to power save mode, and just sits there.  It will not boot into the terminal like I was expecting.  Anyone know why?  If I end up removing most of ubuntu-desktop, is there something else I should install?

My system:
AMD X2 3800, ATI x800GTO.  My intent of the server, for now, is to be a file and print server.

Thanks for any help.

---

