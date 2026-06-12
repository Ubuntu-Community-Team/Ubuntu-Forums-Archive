---
title: "Ubuntu 13.10 and Cairo-dock no longer working correctly"
date: 2013-09-21
forum: Ubuntu Development Version
---

### Post by Hazzabin on 2013-09-21
Ubuntu 13.10 Unity

Last update kernel 3.11.0-8 has changed the cairo-dock behavior, use to be able to click on an active icon and would immediately go to the respective
workspace it was opened on............this now no longer happens.

Any ideas on how to repair/fix this issue........and yes I do know that 13.10 is still in 'Beta' mode

thanks

---

### Post by squilla-dave on 2013-09-26
I can confirm this - clicking the icon no longer takes one to the opened app.

---

### Post by wgarcia on 2013-09-26
It seems as the same issue that is hapenning in the Unity launcher:

[http://ubuntuforums.org/showthread.php?t=2175823](http://ubuntuforums.org/showthread.php?t=2175823)

---

### Post by Hazzabin on 2013-09-26
As of 5 minutes ago with update and reboot it is still not working

what is strange that booting/switching into Gnome within the same OS (Ubuntu 13.10) with kernel 3.11.0-8 Cairo-dock and side dock functions as it should

So certainly the Unity devs have got some work to do

---

### Post by Mateusz Stachowski on 2013-09-27
That bug has been already disscused in another thread titled: [Virtual desktops change?]("http://ubuntuforums.org/showthread.php?t=2175823")

I've [pointed]("http://ubuntuforums.org/showthread.php?t=2175823&p=12796039#post12796039") out that it has [Fix Commited]("https://bugs.launchpad.net/compiz/+bug/1228352") and release scheduled for Compiz 0.9.10.2 and now also 0.9.11.0. This will probably land before final 13.10 release.

---

### Post by Mateusz Stachowski on 2013-09-27
That [bug]("https://bugs.launchpad.net/compiz/+bug/1228352") was fixed in the package compiz - 1:0.9.10+13.10.20130920-0ubuntu1 but it will take some time until this hit the repos.

---

### Post by cariboo on 2013-09-27
> **Mateusz Stachowski said:**
> That [bug]("https://bugs.launchpad.net/compiz/+bug/1228352") was fixed in the package compiz - 1:0.9.10+13.10.20130920-0ubuntu1 but it will take some time until this hit the repos.

I just upgraded to compiz (1:0.9.10+13.10.20130927.1-0ubuntu1) from the repositories, and the problem is solved.

---

