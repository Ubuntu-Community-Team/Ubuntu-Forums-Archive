---
title: "Wat's the correct procedure to install fluxbox from a server installation of ubuntu?"
date: 2006-02-01
forum: Server Platforms
---

### Post by Akhran on 2006-02-01
I did a clean server installation of ubuntu. On a debian, I would have installed fluxbox with 'aptitude install x-window-system fluxbox' and I'm up and running with a reboot into the login GUI.

With the server installation of ubuntu, I've tried 'aptitude install x-window-system-core fluxbox xterm', but that doesn't get me into the login GUI after a reboot. 'Startx' dropped me back to the commandline console.

Would appreciate if anyone has a working procedure on the installation of fluxbox on ubuntu server to share.

Thanks !

---

### Post by dbw on 2006-02-14
try
[http://ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox](http://ubuntuforums.org/showthread.php?t=116759&highlight=fluxbox)

---

### Post by bupkes on 2006-10-25
My fluxbox installation fails to bring up any app that needs x-terminal-emulator.

Here's what I did:
installed the server version of Dapper on an old box (Pentium II/192MB RAM)

aptitude install menu fluxbox x-window-system-core xdm xterm  (This was suggested as a minimum lightweight system in the ubuntu  user docs for low memory systems)

installed nxclient,nxnode,nxserver from nomachines

I can SSH from my windows box to the server box and muck around on the commandline just fine.

I can login to the server box from my windows box using NX just fine.  The fluxbox desktop appears (/usr/bin/startfluxbox from NXclient).  Synaptic, dillo, firefox work just fine from the right-click menu.  Nano, top, xterm and everything else invoked with x-terminal-emulator fail to load in the desktop.

It seems somethign is wrong with the X setup but this n00b is confused despite many hours sifting through ubuntu, fluxbox, and x related sites.

---

