---
title: "Screenshot"
date: 2012-09-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kuvanito on 2012-09-15
Screenshot time delay is not working,needs to be fixed.I tried to report it at launchpad with no success.

---

### Post by cariboo on 2012-09-15
Using gnome-screenshot, with a 3 second delay works for me.

---

### Post by kuvanito on 2012-09-15
are you taking whole screen or an area?
grabbing an area does not work for me.
got two computers freshly installed this morning and they both have the same symptom
one is an intel and the other an amd(<snip>)

---

### Post by cariboo on 2012-09-15
For whole screen and current window, the delay I set works, for a selection, the screenshot happens shortly after I let the mouse button go, which works the way it should. 

BTW, I'm running an Nvidia based system (Nvidia MCP61 chipset) and AMD II X2 240 CPU and NViidia graphics adapter, with zero problems.

---

### Post by effenberg0x0 on 2012-09-15
> **cariboo907 said:**
> For whole screen and current window, the delay I set works, for a selection, the screenshot happens shortly after I let the mouse button go.

When selecting an area via the third radiobox in gnome-screenshot --interactive, all other controls are disabled ("grayed"). It is not possible to apply affects or a time delay to this screenshot mode. 

This is a design choice / technical limitation of the current code.
```
[18:32:23] ahsl@AL-DESK01:[~/dev]: gnome-screenshot --area --delay=2
Conflicting options: --area and --delay should not be used at the same time.
```

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-09-15
> **cariboo907 said:**
> BTW, I'm running an Nvidia based system (Nvidia MCP61 chipset) and AMD II X2 240 CPU and NViidia graphics adapter, with zero problems.


Well, sometimes AMD/Nvidia runs a little hot indeed:
[http://www.engadget.com/2011/11/16/university-gets-188-million-amd-based-supercomputer-free-copy/](http://www.engadget.com/2011/11/16/university-gets-188-million-amd-based-supercomputer-free-copy/)

[http://i.top500.org/system/177157](http://i.top500.org/system/177157)
[http://i.top500.org/system/177820](http://i.top500.org/system/177820)

I wonder if they're using nouveau.

:)

Regards,
Effenberg

---

