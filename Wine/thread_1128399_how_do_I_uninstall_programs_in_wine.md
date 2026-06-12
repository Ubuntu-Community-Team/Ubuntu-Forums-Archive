---
title: "how do I uninstall programs in wine"
date: 2009-04-17
forum: Wine
---

### Post by ricdtinsley on 2009-04-17
I've uninstalled the program but the registery key is still there.

---

### Post by hikaricore on 2009-04-17
Sounds a lot like Windows eh?
You may want to try removing the registry key manually if you know where it is.

> regedit

---

### Post by u235sentinel on 2009-04-17
> **ricdtinsley said:**
> I've uninstalled the program but the registery key is still there.

Under windows I've run ccleaner which usually did a good job of keeping my registery in respectable shape.  Of course that was during my Windblows days.

I guess you can try running ccleaner under WINE and see if it will clean your registery for you.  Something to try.

---

### Post by amingv on 2009-04-17
> **u235sentinel said:**
> Under windows I've run ccleaner which usually did a good job of keeping my registery in respectable shape.  Of course that was during my Windblows days.

I guess you can try running ccleaner under WINE and see if it will clean your registery for you.  Something to try.

I have, in fact, done this. It works.

If by any chance what you´re trying to say is that you uninstalled a program, but the program still appears in the uninstall menu (this has happened to me more often than I´d like), delete the key

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\<name_of_program>
```

In many cases, CCleaner won´t delete this key, so you may have to do it manually (through regedit).

---

### Post by NightMKoder on 2009-04-17
In most cases, why would you need to? If you keep your programs in bottles (by using `env WINEPREFIX=~/.wine/office2007` before wine commands), then when you need to uninstall something, just delete that bottle. In most cases nobody really cares about uninstall working on wine.

Or if you don't want to bother with that, I know crossover has GUI bottles.

---

### Post by StormRoBoT2 on 2009-05-06
use revo uninstaller

> [http://ubuntuforums.org/showthread.php?p=7225617#post7225617](http://ubuntuforums.org/showthread.php?p=7225617#post7225617)

---

