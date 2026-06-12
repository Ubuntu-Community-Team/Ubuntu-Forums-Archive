---
title: "Can I disable the screen going black when it's idle?"
date: 2010-12-11
forum: Server Platforms
---

### Post by anthony62490 on 2010-12-11
Well, not sure I can elaborate much on this. How do I stop the screen from turning black after it's been idle?

Running Ubuntu 10.10 Server

---

### Post by anthony62490 on 2010-12-19
System > Preferences > Power Management gave me an option pertaining to this:

```
Put display to sleep when inactive for: **Never**
```

This option had no effect on the display. Anything else I can try?

---

### Post by brettg on 2010-12-19
I assume from your second post that the "Server" you are running has the full gnome-desktop installed. 

Have you tried disabling the screensaver?

---

### Post by anthony62490 on 2010-12-22
Oh, wow. I just completely sidetracked my own thread. Sorry, that second post was supposed to go in a different place.

The answer is no, the server has no gnome desktop. It's all text-based.

---

### Post by Jose Catre-Vandis on 2010-12-22
Try:
```
setterm -blank 0
```

also

```
setterm -powersave off
```
```
setterm -powerdown 0
```

---

### Post by anthony62490 on 2010-12-24
```
setterm -blank 0
```
Okay, good.
```
setterm -powerdown 0
```
Okay, also good.

```
setterm -powersave off
**cannot (un)setpowersave mode**
```
Google says that I need to kill X Windows before I can use this option, but I don't think I need to tell you that I don't have X Windows. I'll keep looking for the answer, but in the meantime I'll just leave this here.

EDIT: Okay, the server has been running for a while now, so I forgot that I was running under the Screen window manager. So I closed Screen and tried it again. It seems to work, but I'll give it a few minutes.

EDIT2: Okay, it's been running for about half an hour now and it still hasn't gone dark. Thanks for the help, man! o/

---

