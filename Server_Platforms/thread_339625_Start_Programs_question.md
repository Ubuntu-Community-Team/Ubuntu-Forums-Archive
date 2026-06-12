---
title: "Start Programs question"
date: 2007-01-16
forum: Server Platforms
---

### Post by yellowtip on 2007-01-16
Hi,

This is probably a real newby question, but I'm gonna ask it anyway. Any help would be highly appreciated.

I need to launch a program at boot time of Ubuntu 6.0.6 LAMP Server.

To start the program, we have the following shell script:
```

#!/bin/bash

export YT_LICENSE=XXXXXXXXXXXXXXXXXXXXXX
/var/ytrifc/ytrifc -c /var/ytrifc/conf/config.xml -D
```

I read on this forum that to start at boot time I simply needed to place the above shell script into the /etc/init.d/ directory. Unfortunately that doesn't seem to work.

Could anybody please explain to me how to get this to work?

Thanks in advance!

YellowTip

---

### Post by Wim Sturkenboom on 2007-01-16
You must also provide a symbolic link in rc2.d (if your system boots into runlevel 2. As an alternative, you can cut and past the script into rc.local.

---

### Post by mizar001 on 2007-01-16
Also make sure that the script you put in /etc/init.d  has executable flag active.

---

### Post by kitman420 on 2007-01-16
> **Wim Sturkenboom said:**
> You must also provide a symbolic link in rc2.d (if your system boots into runlevel 2. As an alternative, you can cut and past the script into rc.local.

There's a command t hat does this for you. 

Run

```
 update-rc.d -f init_script_name start 90 3 4 5 . stop  1 3 4 5 .
```

This will start your script with priority 90 in run levels 3, 4, and 5 and stop your script in runlevels 1, 3, 4, and 5 when the shutdown command is issued.

D

---

### Post by Wim Sturkenboom on 2007-01-16
Thanks kitman420, will try to remember that one. I'm not really an Ubuntu man. With a Slackware background I'm used to do things manually.

---

### Post by yellowtip on 2007-01-16
Thanks guys! You really helped me out.

My system does indeed start at run level 2. (whatever a runlevel may be).

Could someone please tell me the difference between the rc2.d, rc3.d, etc.  and rc.local?

Thanks in advance!

---

### Post by Wim Sturkenboom on 2007-01-17
rc2.d is for runlevel 2, rc3.d for runlevel 3.
rc.local is executed after rcX.d (replace X by number), regardless of the original runlevel.

Runlevels are used to influence what is started at boot.
Usually, runlevel 0 is used for shutdown and 6  for reboot, runlevel 1 is single user mode for maintenance.
Runlevels 2, 3, 4 and 5 depend on the distro. Usually runlevel 3 does not start the x-server (so you only have textbased login) and runlevel 4 (i.e. Slackware) or 5 (i.e. RedHat) do start the x-server (so you have the GUI).
Ubuntu works slightly different (runlevel 2 is GUI) and I have not found yet how to start it in text-mode.

---

### Post by yellowtip on 2007-01-17
Wim, 

Thanks so much for that explanation. Very informative.

Like this, each day I learn more about this amazing OS.

Thanks!

---

