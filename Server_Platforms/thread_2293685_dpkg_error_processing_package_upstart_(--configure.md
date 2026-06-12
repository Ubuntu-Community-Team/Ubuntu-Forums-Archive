---
title: "dpkg: error processing package upstart (--configure)"
date: 2015-09-06
forum: Server Platforms
---

### Post by cosma-it on 2015-09-06
atm we don't see the wood cause of too much trees ... can help us someone out with the correction of this error? 

invoke-rc.d: initscript udev, action "restart" failed.
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on udev (>= 166-0ubuntu4); however:
  Package udev is not configured yet.


dpkg: error processing package plymouth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mountall:
 mountall depends on udev; however:
  Package udev is not configured yet.
 mountall depends on plymouth; however:
  Package plymouth is not configured yet.


dpkg: error processing package mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on mountall; however:
  Package mountall is not configured yet.


dpkg: error processing package upstart (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 udev
 plymouth
 mountall
 upstart
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by v3.xx on 2015-09-07
Tell us which *buntu and version you are running.

---

### Post by cosma-it on 2015-09-07
Hi 

Server = Ubuntu 14.10 (GNU/Linux 2.6.32-042stab108.8 x86_64)

---

### Post by patlkli on 2015-09-07
You can try ```
sudo apt-get -f install
```

If that still fails, try looking in the syslog:
```
sudo tail -30 /var/log/syslog
```

If there isn't a valuable error message, try looking for recent logs from Upstart services using:
```
ls -ltr /var/log/upstart
```
and then the tail command from above on the appropriate log file.

---

### Post by Bashing-om on 2015-09-07
cosma-it; Hello;

> **cosma-it said:**
> Hi 

Server = Ubuntu 14.10 (GNU/Linux 2.6.32-042stab108.8 x86_64)

Release 14.10 is End_Of_Life and no longer has support. The software repository by now may have been removed.
In addition is the old 12.04 kernel that you are running.

Is it time for a fresh clean install of say 14.04 ( support 'til April 2019 ) ?


[INDENT][INDENT]why beat on a dead horse
[/INDENT][/INDENT]

---

### Post by cosma-it on 2015-09-07
> **Bashing-om said:**
> cosma-it; Hello;



Release 14.10 is End_Of_Life and no longer has support. The software repository by now may have been removed.
In addition is the old 12.04 kernel that you are running.

Is it time for a fresh clean install of say 14.04 ( support 'til April 2019 ) ?

[INDENT][INDENT]why beat on a dead horse
[/INDENT]
[/INDENT]


never change a "dead" running system, active domains on it .. 

fear to touch it ... when i wreck with an update it the boss shoot me :D

---

### Post by Bashing-om on 2015-09-07
cosma-itl Yukkie;

Running an End_if_life release ... no security updates, no updates of any nature. A disaster for a production server to be in !

Best have a long heart-2-heart talk with the boss.
14.04 for the win !- Long Term Support -

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by patlkli on 2015-09-08
cosma-it sent my the log files I asked for in private, however there were no indications of any errors happening in there.

> **Bashing-om said:**
> cosma-itl Yukkie;

Running an End_if_life release ... no security updates, no updates of any nature. A disaster for a production server to be in !

Best have a long heart-2-heart talk with the boss.
14.04 for the win !- Long Term Support -

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

I agree. You really shouldn't be running a system with an OS which reached End of Support. 
*Especially *not a system with direct exposure to the Internet like yours with domains hosted on it.

---

### Post by cosma-it on 2015-09-08
yes, i will move on the weekend the whole server to a 14.04 server ... hope all will work out :)
then will get renewed :) 
thanks for your help guys :)

---

### Post by Bashing-om on 2015-09-08
cosma-it; :)

Any problems in the upgrade; we are here to help/ Let us know how it goes and when you are back up.

[INDENT][INDENT]it is a big thing
[/INDENT][/INDENT]

---

