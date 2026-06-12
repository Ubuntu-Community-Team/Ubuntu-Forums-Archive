---
title: "Vmware 2.0.1 manual start"
date: 2009-09-16
forum: Virtualisation
---

### Post by fernandoch on 2009-09-16
Hello,

How can I disable vmware 2.0.1 from starting after each reboot?

And then how to start it manually?

I need something like chconfig on redhat...

Thank you.

---

### Post by lensman3 on 2009-09-17
Delete the "ln -s" links in /etc/rc3.d and /etc/rc5.d.  That will break the boot startup.  The vmware will have a S??vmware where the ?? is order the daemons will start during boot.  Look up info on SYS5 boot sequencing.  If the -s link looks like K??vmware then that is the shutdown sequence number. "K" stands for kill process, since stop and start both start with the same letter!  It is probably OK to leave the "K"s where they are.

To start vmware at other times do:  "/etc/init.d/vmware start" or restart to restart the daemons.  You will have to check the exact name for /etc/init.d/vmware (the /etc/init.d is OK, it is the vmware name I'm not sure of).  This script is what the "S??" and the "K??" are actually linked to.

Hope this helps.

---

### Post by fernandoch on 2009-09-17
Thank you for the reply, but why runlevels 3 and 5?

Ubuntu uses runlevel 2 by default, isn't it?

---

