---
title: "System freezes after resume from suspend"
date: 2013-04-12
forum: Ubuntu Development Version
---

### Post by treesurf on 2013-04-12
Howdy all,  I have searched this forum and launchpad and have not found any good matches for this same problem I am having.

Issue: Laptop resumes normally from suspend, login no problem.  However, within 30 seconds of resuming to the desktop keyboard and mouse activity hangs and the whole system is unresponsive.  Only solution is to cut power and reboot.  This does not happen every time, and I have not found any pattern yet.

Anyone else having this problem, or know a workaround?  Should I start a bug report on launchpad?

Thanks!

---

### Post by Toz on 2013-04-12
What is the make/model of the computer?

You might also consider posting relevant info from /var/log/dmesg, /var/log/syslog, and /var/log/Xorg.0.log around the time of the resume until the hang. There may be some information there that might be helpful.

---

### Post by treesurf on 2013-04-13
It's a Lenovo Ideapad Y550 laptop with integrated Intel GM45 chipset.  I'll see if it's possible to grab that info next time it happens.

---

### Post by akgrant on 2013-04-13
How locked up is it?  Can you get to a tty terminal (Ctrl-Alt-F2 - F6, Ctrl-Alt-F7 to return to X)?  Maybe restarting lightdm is enough.

---

### Post by sgage on 2013-04-13
Do you have Nvidia graphics? With the stock open-source nouveau drivers, my computer has never resumed from sleep without freezing up. Works fine with the proprietary nvidia drivers....

---

### Post by treesurf on 2013-04-16
It's totally locked up.  No ability to get to a tty terminal.  And my machine has integrated intel graphics, not Nvidia.


On the plus side it hasn't happened for a couple days so I'm crossing my fingers that one of the updates fixed it.

---

