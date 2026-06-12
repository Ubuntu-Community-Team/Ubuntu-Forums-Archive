---
title: "Start a program on startup"
date: 2007-03-21
forum: Server Platforms
---

### Post by jesusrop on 2007-03-21
I'm setting up an Ubuntu server and also want it to use lphant in it, wich is now working. I'd like lphnant to automatically startup when Linux loads (even before loging in to it), but I don't know how.

The command to run lphant is

xurra@vmserver:~$ mono ~/LphantCmdLine.exe

I think I should add it to some init configuration file, but I don't know haow to do it.

Command line instruction only, as I don't have any desktop enviorement installed.

Thanks a lot!!!

---

### Post by MikeDX on 2007-03-21
I thinkthe easiest way would be to make a script with that line, chmodded to +x and copied to /etc/init.d

that way it will be run as soon as the machine starts. I think all init.d scripts run as soon as the os is "ready"

---

### Post by tomchuk on 2007-03-21
Easy way: just add a "mono /home/whoever/LphantCmdLine.exe &" to /etc/rc.local
Hard way: create a proper init script in /etc/init.d/ with proper start, stop, restart functions and add it to runlevels with update-rc.d

---

