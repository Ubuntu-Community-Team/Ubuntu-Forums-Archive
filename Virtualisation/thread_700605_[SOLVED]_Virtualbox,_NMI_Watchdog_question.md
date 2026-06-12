---
title: "[SOLVED] Virtualbox, NMI Watchdog question"
date: 2008-02-18
forum: Virtualisation
---

### Post by FuturePilot on 2008-02-18
Ok, kind of silly question. I noticed these logs after installing Virtualbox
```
Feb 18 14:21:57 GutsyGibbon kernel: [ 7852.071516] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Feb 18 14:21:57 GutsyGibbon kernel: [ 7852.071523] vboxdrv: Successfully done.
```
So my question is, is it safe to disable NMI Watchdog? Is this going to have any negative effects on my system? What exactly is it anyway?

---

### Post by randy78 on 2008-02-18
[http://www.slacksite.com/slackware/nmi.html]("http://www.slacksite.com/slackware/nmi.html")

---

### Post by FuturePilot on 2008-02-18
Thanks for the link. Apparently it wasn't even activated in the first place since in order to use NMI Watchdog you need to add a parameter to the kernel. So that answered all my questions. Thanks :)

---

### Post by randy78 on 2008-02-18
Cool
Glad to help! :D

---

