---
title: "Request for help from a Linux Newbie"
date: 2007-07-12
forum: Windows
---

### Post by supportbroker on 2007-07-12
I just installed the Wine Windows app (I think) I mean it shows up in the add/remove applications list and I can't figure out where it is or get it to run...I mean there is no icon on my desktop or drop down on my taskbar...Where is it? and how can I get it to run?

Help

---

### Post by Paul820 on 2007-07-12
I usually have to reboot to get that to show up. To configure it, go to terminal and type: winecfg, that will well you the configuration editor. Try a reboot and it should turn up in a menu entry on it's own.

---

### Post by qamelian on 2007-07-12
Wine doesn't show up in the Applications menu unless you have actually used it to install at least one Windows application. Then you will see an entry for Wine that contains a sub-menu for the application(s) you have installed.

To install a Windows application using Wine, open a terminal and type:
```
wine /path/to/installer/installername
```

For example, if the program is on a CD with an installer named setup.exe in the root directory of the CD, you would type:

```
wine /media/cdrom/setup.exe
```

---

