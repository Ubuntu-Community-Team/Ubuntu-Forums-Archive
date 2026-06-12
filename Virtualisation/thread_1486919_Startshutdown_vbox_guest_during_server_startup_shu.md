---
title: "Start/shutdown vbox guest during server startup shutdown."
date: 2010-05-18
forum: Virtualisation
---

### Post by nlinecomputers on 2010-05-18
I have a Ubuntu server 8.04, no GUI except webmin, running a headless virtualbox with a Windows Xp Pro guest.  I need to be able to start the vbox guest on bootup of the server and on shutdown.

Ideas?

Thanks.

---

### Post by opacatica on 2010-05-21
You can use VBoxManage CLI for managing your virtual machines.  Command may be all lowercase depending if you have OSE or PUEL version of VBox.
 
[http://www.virtual-box.de/manual/ch08.html](http://www.virtual-box.de/manual/ch08.html)
 
I have full GUI but used this CLI to create a quick launch button in my task bar.  While at it I suggest you use CRON to schedule a regular check make sure your guest systems are still running, perhaps emailing you about failures...

---

