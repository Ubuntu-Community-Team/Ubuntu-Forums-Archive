---
title: "Suspend/Hibernate/Blank Screen"
date: 2013-09-17
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2013-09-17
Here is the situation.. I have the following setings:

Dim to save power:  unchecked


Turn screen off when inactive:  never

Lock:  off

require my password when waking from suspend:  off

Plus I added xset s 00 to .profile

Then I rebooted and when I stepped away for a few minutes, my screen was blank, when I returned,  about 5 minutes later I estimate.  So what else do I need to do to stop the screen from blanking.

Henry

---

### Post by VinDSL on 2013-09-17
> **Hewjr100 said:**
> So what else do I need to do to stop the screen from blanking.
Here's what I use:

```
xset s off && xset dpms force on && xset -dpms
```

To check the status:

```
xset q | grep -A1 -i dpms
```

Resets on boot/restart.

I suppose you could set it to autoload at startup...

---

### Post by Hewjr100 on 2013-09-17
Nope, did the same thing, 5 minutes and blank.  Well at least it only happens when I am not doing anything.

Henry

---

