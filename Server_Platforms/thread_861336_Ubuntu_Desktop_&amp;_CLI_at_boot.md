---
title: "Ubuntu Desktop &amp; CLI at boot"
date: 2008-07-16
forum: Server Platforms
---

### Post by UncleAelfrich on 2008-07-16
I have installed a server install from the server install CD.

Then I installed ubuntu-desktop. [PLEASE - I have read many of the threads where those who would install a GUI on their servers are considered untouchable Philistines (to mix metaphors) and deserve to be summarily executed. A repetition of those sentiments here will not be useful.]

What I would like to do is to set up a menu choice that upon booting up, I can have the choice to a)boot into a CLI, or b)boot into the desktop. I remember a few years ago when I built a Gentoo box we had such a menu. [And YES, I even did a stage 1 install.] But I cannot find in Ubuntu a way to do the same.

Can someone please point me to a way to do this? [Design the menu choice, that is. I have NO DESIRE to do a stage 1 optimization of the Ubuntu kernel.]

[I think the menu would be done through the /boot/grub/menu.lst by commenting out the "quiet" command, lengthening the wait interval, and adding the start command for /bin/bash, but I could be wrong]

Thanks for your help

---

### Post by HermanAB on 2008-07-16
Yes, you need to add a Grub menu entry to run in either level 3 or level 5.

---

### Post by cdenley on 2008-07-16
> **HermanAB said:**
> Yes, you need to add a Grub menu entry to run in either level 3 or level 5.

Ubuntu will boot up to a GUI for runlevels 2-5 by default. You can stop it from loading a GUI on runlevel 2
```

sudo rm /etc/rc2.d/*gdm

```
then change your grub configuration to boot to different run levels. 2 for CLI; 3, 4, or 5 for GUI.

---

### Post by windependence on 2008-07-16
Yes, you have all the tools you need at your fingertips. You can configure runlevel 3 to be just non-GUI, and 5 to be GUI (or however you want it) and then just type your option at the boot prompt.

-Tim

---

