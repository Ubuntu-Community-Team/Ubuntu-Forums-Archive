---
title: "Lenovo Z570 vs Suspend"
date: 2013-03-16
forum: Ubuntu Development Version
---

### Post by mykrob on 2013-03-16
Evening, all
As the title suggests, I have a Lenovo Z570. Works great, except if I try to suspend the laptop. it seems I have a 50/50 chance of the screen coming back on.

Looking for troubleshooting steps to hopefully achieve a proper suspend on this laptop.
THanks

---

### Post by Toz on 2013-03-16
Of interest would be the log file **/var/log/pm-suspend.log** noting which set of log entries relate to a successful resume and which log entries relate to an unsuccessful resume. (Perhaps its just an issue with the screen backlight not returning on resume - for which the kernel parameter **acpi_backlight=vendor** might help).

Here are a couple of wiki articles on debugging suspend/resume:
- [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume")
- [https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend")

---

### Post by mc4man on 2013-03-16
You also _may_ want to take a look at this thread, while you didn't say figure the laptop has intel graphics - 
[http://ubuntuforums.org/showthread.php?t=2126215](http://ubuntuforums.org/showthread.php?t=2126215)

(- on an older Dell 1330m w/ GeForce 8400M GS suspend does not work, (return from),  with nouveau, does work fine  with nvidia drivers

---

