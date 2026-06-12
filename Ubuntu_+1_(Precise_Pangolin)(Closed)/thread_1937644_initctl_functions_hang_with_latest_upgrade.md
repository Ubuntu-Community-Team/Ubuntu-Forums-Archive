---
title: "initctl functions hang with latest upgrade"
date: 2012-03-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jelijami on 2012-03-08
With my latest upgrade, initctl hangs.

While running apt-get upgrade, the install hung.

ps fax shows:
```
16314 pts/4    S+     0:00  |       \_ /bin/sh /var/lib/dpkg/info/modemmanager.postinst configure 0.5.1.96+git2012020818
07.635fce1-0ubuntu3
16315 pts/4    S+     0:00  |           \_ /bin/sh /usr/sbin/invoke-rc.d modemmanager start
16331 pts/4    S+     0:00  |               \_ /bin/sh -e /etc/init.d/modemmanager start
16333 pts/4    S+     0:00  |                   \_ status modemmanager
16334 pts/4    S+     0:00  |                   \_ grep -q  start/

```

When I kill the hanging 'grep', 'status', and 'init.d' processes, the install continues, until it hits another service that needs to be stopped/restarted/reloaded. There it hangs again.

Killing the offending processes every time the install script stalls, will get me out of it, with a 'too many errors' message.


Apparently, it's the 'initctl' command that's at fault.
Running 'initctl list', for example, will just sit there, producing no output. Ctrl-C gets me out of it.

I have reinstalled the upstart package, to no avail.

---

### Post by jelijami on 2012-03-08
More info:

. the 'init' process is hogging one CPU
. a process listing with 'ps fax' comes up with a lot (243) <defunct> processes

---

### Post by jelijami on 2012-03-09
Did the following:

```
# cp /sbin/initctl /sbin/initctl.old
# vi /sbin/initctl
[INDENT]#!/bin/bash
exit 0[/INDENT]
```
This allowed dpkg to clean things up:
```
# dpkg --configure -a
```
Restore 'initctl':
```
# mv /sbin/initctl.old /sbin/initctl
```

The upgrade came with a new kernel, so I had to rebuild the created initramfs:
```
# dpkg-reconfigure initramfs-tools
```

After a reboot (power button), everything runs fine now.

---

### Post by cariboo on 2012-03-09
Marked as solved, as the op found a solution to his problem.

---

