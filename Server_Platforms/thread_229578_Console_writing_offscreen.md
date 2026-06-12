---
title: "Console writing offscreen"
date: 2006-08-04
forum: Server Platforms
---

### Post by echeadle on 2006-08-04
When the system boots the console starts below my screen and lines write above the top.  This has never happened to me in any distribution, so I am at a loss. Most of the fixes for resolution problems happen in X, but this is not in X. Is there somewhere you can tweek the console?  Usually I would just auto adjust the monitor and call it good.  

Any help is appreciated.

---

### Post by MJN on 2006-08-04
What's the reason for you not adjusting the monitor? Given the low(er) resolution any monitor adjustments shouldn't affect your main (higher res) X display and should only require doing the once.

Given you already know about this method though I guess it's not satisfactory... but why?

Mathew

---

### Post by natrixgli on 2006-08-07
Try adding the boot parameter:

```
VGA=773
```

To /boot/grub/menu.lst


I've experienced the same problem on multiple installs. On LCD displays you cannot adjust the screen dimensions enough to compensate, which makes operation difficult!

-n8

---

