---
title: "[SOLVED] XP taskman in virtualbox"
date: 2008-09-05
forum: Virtualisation
---

### Post by kevmitch on 2008-09-05
Ok, maybe I'm missing something really stupid, but I can't get task manager to open in an XP guest in VirtualBox 1.6.6 (the closed source edition) or virtualbox-ose 1.6.4 (open source edition). It's highly unlikely that this is related to any sort of malware as it is observed on a fresh install of XP. I've even tried using two separate XP install discs and I get the same thing.

---

### Post by prshah on 2008-09-05
> **kevmitch said:**
> I can't get task manager to open in an XP guest 

Have you tried _all_ the following methods?

1) Machine-Insert Ctrl+Alt+Del (to client)
2) Start-Run-```
taskmgr.exe
```
3) Press Ctrl+Esc
4) Start-Run-```
cmd.exe
``` Then ```
start taskmgr.exe
```

Do you get any permission errors? Or does it just get silently ignored?

---

### Post by kevmitch on 2008-09-05
Ok, I'm a complete idiot. Alt-Ctrl-Del doesn't work because its being caught by my host window manager. Ok, fine, I kind of expected that, so I had been trying to run <b>taskman.exe</b> from the Run menu and/or cmd.exe. It never gave me an error and on the command line it just returned a new prompt with no feedback. Of course <b>taskmgr.exe</b> works fine. Sorry, it's been a while since I've used Windows, thanks.

---

