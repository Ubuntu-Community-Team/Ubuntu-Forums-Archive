---
title: "Virtual desktops change?"
date: 2013-09-21
forum: Ubuntu Development Version
---

### Post by miguelpires on 2013-09-21
Hi,
The problem I'm facing is this:
Before the today upgrade, and if I've some app open in desktop 1, desktop 2, desktop 3, i click on the icon of that app and the system go to the app that is in another Desktop.
After today update is not more possible to do that. Anyone notice this beavior?
Regards
Miguel

---

### Post by PJs Ronin on 2013-09-21
Confirmed.

---

### Post by miguelpires on 2013-09-21
Is trhis a new feature or a bug?

---

### Post by grahammechanical on 2013-09-21
Still works for me. Ubuntu Unity 13.10. And I have just loaded this installation and updated it. Try updating again or rebooting.

Regards.

---

### Post by miguelpires on 2013-09-21
Not for me. I rebooted and still same behaviour...

---

### Post by PJs Ronin on 2013-09-21
> **grahammechanical said:**
> Still works for me. Ubuntu Unity 13.10. And I have just loaded this installation and updated it. Try updating again or rebooting.

Regards.

Rebooted twice, 7 hours sleep, 3 cups of coffee, some high sugar snacks and an argument with my neighbour and 13.10/Unity is still acting as per OP.   I'm not sure if it's a bug or new feature.

Also to be noted is that in 13.04 and earlier in 13.10, if I started an application in workspace 2 but quickly changed to workspace 1, the application would follow me to workspace 1... most inconvenient.   With recent updates to 13.10 if I now open an application in workspace 2 and quickly mouse to workspace 1, the application stays in workspace 2.   This is good... specially if you're starting something like Virtualbox from a VDI that is going to shoot fullscreen/seemless.

---

### Post by cariboo on 2013-09-21
I've run into the same problem, and after a reboot still no joy. I have to admit that I didn't notice if the problem was there this morning before I went to bed, but I did do an update just before heading off, and noticed the problem when I logged in after getting up this afternoon.

---

### Post by Mateusz Stachowski on 2013-09-22
I also have the bug described in this thread. I have it in my  virtualized 13.10 (VirtualBox) and in the iso image (synced today)  booted directly with the help of grml-rescueboot which creates a grub  menu entries for iso images.

There were upgrades to both [Unity]("https://launchpad.net/ubuntu/+source/unity/7.1.0+13.10.20130920-0ubuntu1") and [Compiz]("https://launchpad.net/ubuntu/+source/compiz/1:0.9.10+13.10.20130920-0ubuntu1")  recently. Those updates introduced also another bug with minimalization  of all windows (showing desktop). To reproduce that bug use the  shortcut CTRL + Super + D or in the Alt + Tab select the show desktop  and then repeat that to unminimize the windows. Now try to move windows  while clicking on the decoration. You will see that you can't move  window and the decoration becomes inactive. If you had windows stacked  one on another you will get a click through the decoration to window  below the current one.

This bug is another incarnation of the bug [#1158267]("https://bugs.launchpad.net/compiz/+bug/1158267") but this time it doesn't  have anything to do with maximized windows.

---

### Post by Mateusz Stachowski on 2013-09-22
I have a half good news about the workspace switching bug. The devs [solved]("https://code.launchpad.net/~townsend/compiz/fix-auto-vp-switch-0.9.10/+merge/186881") it and the fix is commited and scheduled for release in Compiz 0.9.10.2 but it looks like they will need to revisit this [bug]("https://bugs.launchpad.net/compiz/+bug/1092323").

---

### Post by miguelpires on 2013-09-24
No news about this?

---

### Post by mc4man on 2013-09-24
> **Mateusz Stachowski said:**
> I also have the bug described in this thread. I have it in my  virtualized 13.10 (VirtualBox) and in the iso image (synced today)  booted directly with the help of grml-rescueboot which creates a grub  menu entries for iso images.

There were upgrades to both [Unity]("https://launchpad.net/ubuntu/+source/unity/7.1.0+13.10.20130920-0ubuntu1") and [Compiz]("https://launchpad.net/ubuntu/+source/compiz/1:0.9.10+13.10.20130920-0ubuntu1")  recently. Those updates introduced also another bug with minimalization  of all windows (showing desktop). To reproduce that bug use the  shortcut CTRL + Super + D or in the Alt + Tab select the show desktop  and then repeat that to unminimize the windows. Now try to move windows  while clicking on the decoration. You will see that you can't move  window and the decoration becomes inactive. If you had windows stacked  one on another you will get a click through the decoration to window  below the current one.

This bug is another incarnation of the bug [#1158267]("https://bugs.launchpad.net/compiz/+bug/1158267") but this time it doesn't  have anything to do with maximized windows.
I believe that behavior with 'show desktop' minimised windows came from something in the unity upgrade. 
(whether the big commit to compiz is a factor not sure but reverting it has no effect while downgrading unity to previous version does eliminate the issue...

Edit: - bug here on unity, fixed but not yet released
[https://bugs.launchpad.net/unity/+bug/1228915](https://bugs.launchpad.net/unity/+bug/1228915)

---

