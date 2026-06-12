---
title: "Problems with new procps (3.2.8-11ubuntu2)"
date: 2011-11-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-11-16
The newest procps (3.2.8-11ubuntu2) installation causes problems on both 32-bit and 64-bit setups. This is what happens:

> 
Setting up procps (1:3.2.8-11ubuntu2) ...
Installing new version of config file /etc/init/procps.conf ...
start: Unknown parameter: UPSTART_EVENTS
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1


And here is the bug (771372) report:
[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/771372](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/771372)

---

### Post by 3vi1 on 2011-11-16
Yep... seeing it too.

---

### Post by ventrical on 2011-11-16
same here:

fix on the way.

---

### Post by Harry33 on 2011-11-17
Now this has been fixed, by reverting the previous change (3.2.8-11ubuntu3).

Another bug report (891369) here:
[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/891369](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/891369)

It says it broke upgrading. Well I downgraded to the previous version (3.2.8-11ubuntu1) yesterday and that fixed this too.

---

### Post by paul_in_london on 2011-11-17
Yep, procps (**1:3.2.8-11ubuntu3**) installs ok:

```
...Setting up libperl5.14 (5.14.2-4) ...
Setting up libdconf0 (0.10.0-2) ...
Setting up procps (1:3.2.8-11ubuntu3) ...
procps stop/waiting
Setting up libisc62 (1:9.7.3.dfsg-1ubuntu5) ...
Setting up libdns69... 
```

---

### Post by Harry33 on 2011-11-18
The new update of procps (3.2.8-11ubuntu4) fixes this issue.

---

