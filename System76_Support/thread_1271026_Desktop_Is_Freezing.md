---
title: "Desktop Is Freezing"
date: 2009-09-20
forum: System76 Support
---

### Post by flukeairwalker on 2009-09-20
My Pangolin has been freaking out lately. The screen freezes and the desktop won't refresh. This usually happens on actions such as minimize, maximize, opening a new window, and switching desktops. Originally I thought it was only happening when I had Pidgin open but now it turns out it's happening all the time. Included are the logs and a screenshot. I don't do anything crazy with my computer, just normal home user stuff. What's going on?

Edit: I have a feeling it's something to do with the graphics.

---

### Post by Ed.Corcoran on 2009-09-20
Try disabling Desktop Effects (it's under System>Preference>Appearance). That might help. If it doesn't, at least we know Compiz isn't the problem.

---

### Post by jdb on 2009-09-20
> **flukeairwalker said:**
> My Pangolin has been freaking out lately. The screen freezes and the desktop won't refresh. This usually happens on actions such as minimize, maximize, opening a new window, and switching desktops. Originally I thought it was only happening when I had Pidgin open but now it turns out it's happening all the time. Included are the logs and a screenshot. I don't do anything crazy with my computer, just normal home user stuff. What's going on?

Edit: I have a feeling it's something to do with the graphics.

Sometimes things freeze up when the network becomes unavailable.
Your syslog reports your wifi dropped & NetworkManager can't get it back.

jdb

---

### Post by flukeairwalker on 2009-09-20
@ Ed. I have disabled Compiz effects to see if that helps. I wasn't able to duplicate the problem before disabling it, however, so I can't say if it's Compiz acting up yet.

@ jdb. This incident was the first time where network manager dropped on top of the desktop freezing. But I will keep an eye out if it a continuing trend.

---

### Post by flukeairwalker on 2009-10-07
Consider it solved. I found out that my laptop wasn't getting enough fresh air. I stopped keeping it hidden in the keyboard tray of my desk and took it to get the fans cleaned at the local computer store. Since then my laptop has been running more silent, cooler (63C as opposed to 75C before cleaning), and hasn't frozen up one bit.

---

