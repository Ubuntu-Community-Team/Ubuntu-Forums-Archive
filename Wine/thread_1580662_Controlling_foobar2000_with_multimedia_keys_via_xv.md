---
title: "Controlling foobar2000 with multimedia keys via xvkbd and wine"
date: 2010-09-23
forum: Wine
---

### Post by jampe on 2010-09-23
Ahoy!

I can't help it, I'm still in love with foobar2000. It runs beautifully on wine, and with a little bit of fiddling around, it can be integrated nicely alongside the native Linux applications.
The next issue is the multimedia keys, which I have gotten to work, but only when foobar2000 is in focus. I'm running a bash script from the keyboard shortcuts preference application, like so:

**The method:**
In Keyboard Shorcuts under XF86AudioPlay:
```

bash /home/jampe/Scripts/foobar2000/PlayPause.sh

```

In PlayPause.sh:
```

#!/bin/bash
sleep 0.3;
xvkbd -window "Wine" -text "x"

```

(I set "x" as a keyboard shortcut in foobar2000 for play/pause)


**The problem:**
It only works when I manually focus the foobar2000 window. If it's only up to xvkbd's "-window" function, the window is only kind of half-focused, and foobar2000 doesn't respond to keyboard inputs.
xvkbd does this with all wine applications, but with none of the native ones like gedit.

**The cry for help:**
Does this make sense to any of you?
Any help is highly appreciated. I have cookies.

---

### Post by jampe on 2010-09-26
bump.

---

### Post by jampe on 2010-09-27
Hm. Never mind. Apparently I didn't do my research properly on this one:
[http://www.hydrogenaudio.org/forums/index.php?showtopic=54933](http://www.hydrogenaudio.org/forums/index.php?showtopic=54933)

---

