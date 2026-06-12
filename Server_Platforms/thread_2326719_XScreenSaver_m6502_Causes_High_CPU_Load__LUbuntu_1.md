---
title: "XScreenSaver m6502 Causes High CPU Load  LUbuntu 16.04 Server"
date: 2016-06-03
forum: Server Platforms
---

### Post by Markus_Lankeit on 2016-06-03
The new server I had just setup was nearly brought down to its knees with CPU utilization above 50% across all cores!   But, I just barely installed lubuntu 16.04 server--I wasn't running anything yet... some quick research pointed me to a process called "m6502" that was running in multiple iterations (one per CPU core) and that was solely responsible for the excessive load.  

Researching on "m6502," I found it is part of the standard XScreenSaver distribution.  Apparently, the default behavior for XScreenSaver is to randomly pick from the installed screen savers and change every 10 min.  So, sometimes you just get lucky and get the one that consumes your entire system.  I also came across previous posts, noting that XScreenSaver has been causing high CPU loads for nearly a decade.  Previous posts resolved the issue by having the user manually change the screen saver preferences in the GUI.  None addressed how to change this globally, which would be appropriate for a server setting.  After some research, I came across a simple solution that worked for me:

 Edit this file: /etc/X11/Xresources/x11-common

Add this line to the bottom:
>  xscreensaver.mode: blank

Then, restart the window server or reboot the system.  Now, XScreenSaver is set to produce a blank screen (meaning 0 CPU load).  Individual users can still defy this and have their own preferences, but the default system behavior is the blank screen.

As a side-note, m6502 is the absolute worst in causing CPU load of all the screen savers in the distro.  Some of the others also cause CPU load, but not nearly as bad as m6502.  Also, none of the doc's talk about how to uninstall a screen saver... maybe just delete the binary from /usr/lib/xscreensaver?   Finally, why in the world does the server distribution ship with a screen saver that is well known to overload the CPU?  Maybe everyone expects a server to never run a GUI...

---

### Post by howefield on 2016-06-04
Thread moved to the "*Server Platforms*" forum.


> **Markus_Lankeit said:**
> ..... Maybe everyone expects a server to never run a GUI...

Yes, that would be the norm for a server ;)

---

### Post by cariboo on 2016-06-04
If you really need to use a gui on a server, I'd suggest removing lxdm, and the using startx when you need a gui. The best practice is to learn to use the command line via ssh for your server

---

### Post by Markus_Lankeit on 2016-06-09
The point is not really whether or not to install a GUI on a server--and yes, I know about ssh... I've been doing sys-admin work on Unix systems for a number of decades.  Here's one thing I can say from experience: having a light-weight GUI makes life a lot easier, especially when I have to do work on the console.  Therefore, I would argue that "best practice" includes having a GUI readily available.  

That said, the main point really is that "lubuntu minimal" on a "server distribution" installs a screen saver with components that are well known to overload the CPU, yet lubuntu that advertises itself as "lightweight"?

---

