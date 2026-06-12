---
title: "Headless Server from Dapper Desktop Install?"
date: 2006-12-07
forum: Server Platforms
---

### Post by SSTwinrova on 2006-12-07
As I've seen some people mention, I'm going to go with a desktop install of Dapper so that I have the GUI tools for configuring some of the services. However, for normal use, I don't plan on having a monitor (or anything really, just a printer and network cable) connected to the computer. Will this cause problems with X trying to start and the monitor not being present? If so, could someone tell me what startup scripts to remove so that X wouldn't try to start on boot? Thanks.

---

### Post by averagejoe84 on 2006-12-07
If you don't want X to start at all just change the default run level to runlevel 3.. to do this Type sudo vi /etc/inittab and edit the line that reads id:5:initdefault: to id:3:initdefault:

This should do what you want it to do. Let me know if you have any questions

---

### Post by technodigifreak on 2006-12-07
Agrees: changing the default runlevel is the best way to go about it.

however, X can start without issue even if a monitor is not attached to the system.  VNC and/or FreeNX are great remote management GUI tools.  I highly recommend FreeNX because of the encrypted and highly compressed data transmission.

---

### Post by SSTwinrova on 2006-12-07
Hmmm...I may look into one of those options so I can just completely manage it from the computer in my room (I was already planning on having ssh set up for stuff like updating, but this will be nice for when anything "extra" goes wrong  :)).

And thanks about the runlevel suggestion, also. I thought I had read somewhere that all of Ubuntu's runlevels were the same, so I hadn't thought just doing that would be the solution.

---

### Post by chrisfay on 2006-12-08
If you're using Gnome you could also stop the desktop manager by typing:

```
sudo /etc/init.d/gdm stop
```

When you reboot it would ovbiously restart but, you could remove the startup script as well....

---

