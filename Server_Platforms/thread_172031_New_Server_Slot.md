---
title: "New Server Slot"
date: 2006-05-07
forum: Server Platforms
---

### Post by gymsmoke on 2006-05-07
I just noticed that there is a new linux image available for upgrade on my Ubuntu 5.10 server.  Since I only access this server remotely (co-lo), if i run apt-get upgrade , will grub install the latest kernel on reboot, or will it (as most Linuxes do), present a grub menu with choices ?  (Essentially, this list will be presented to _no-one_, since I couldn't see it anyway) ...

Thanks for the feedback... apparently, no one knows the answer to this on the irc channel.

---

### Post by ape on 2006-05-08
The new kernel should be installed if it is showing as being one of the packages upgraded by `apt-get upgrade`.

Whether grub halts at it's menu screen depends on how you have it configured.  You can have it not display any screen and boot the designated kernel entry in the menu.lst file after a certain delay, you can have it display the menu for X number of seconds and then boot the designated kernel automatically, or you can have grub stop at the menu and wait for user input (obviously you don't want this).

How is your /boot/grub/menu.lst file currently configured?

---

