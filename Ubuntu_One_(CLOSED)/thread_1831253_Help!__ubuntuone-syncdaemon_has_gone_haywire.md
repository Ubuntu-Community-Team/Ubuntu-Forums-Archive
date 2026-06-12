---
title: "Help!  ubuntuone-syncdaemon has gone haywire"
date: 2011-08-23
forum: Ubuntu One (CLOSED)
---

### Post by Kissell on 2011-08-23
My PC keeps locking up.  Before it locks up I can see in System Monitor that ubuntuone-syncdaemon is taking up nearly 100% of one of the CPU cores, and it is constantly growing in memory usage.  I have 16GB of RAM and ubuntuone-syncdaemon takes more and more until it is all gone and then I have to press the reset button.  

If I kill the process of ubuntuone-syncdaemon, the process respawns itself and the new one starts growing out of control.  

I have uninstalled and reinstall Ubuntu One, but the problem returns when I reinstall.

The only way I can use my computer is to go to the terminal and kill all ubuntuone processes (not just ubuntuone-syncdaemon).  If I do that before it eats all my memory, then ubuntuone-syncdaemon won't respawn.  

This is on Natty x64.

---

### Post by duanedesign on 2011-08-23
Could you please check if this file contains anything:

~/.cache/ubuntuone/log/.cache/ubuntuone/log/syncdaemon-exceptions.log

thank you,
Duane Hinnen

---

### Post by Kissell on 2011-08-23
I ended up fixing it by deleting a hidden folder in my home directory.

```
sudo rm ~/.local/share/ubuntuone -R
```

After deleting that folder, ubuntu one works like normal again and no longer locks up the computer.

---

