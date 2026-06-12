---
title: "Plasma 5 - kactivitymanagerd crashes when resuming from screen lock"
date: 2014-11-17
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2014-11-17
If anyone else is testing KDE with vivid, I'd be interested in knowing if you're seeing the same thing:

After locking the screen, and letting it sit a bit, trying to resume will always result in a crash that throws me back to the lightdm login.  At times it happens after entering the password, but at others (when screen blanking has kicked in) all I have to do is move the mouse.

```
Nov 17 06:24:23 clevo kernel: [83196.562353] traps: kactivitymanage[4448] general protection ip:7f63639316d5 sp:7fff0e67f398 error:0 in libqxcb.so[7f6363905000+b2000]
```

I run Ubuntu, with the plasma-desktop packages... so this might not be a problem for people running Kubuntu.

**UPDATE**:  Resolved by further package updates.

---

