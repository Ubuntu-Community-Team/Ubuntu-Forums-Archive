---
title: "ubuntu server 10.04 does not start init.d scripts"
date: 2010-05-17
forum: Server Platforms
---

### Post by mgiammarco on 2010-05-17
Hello,
I have two ubuntu servers. I have upgraded them to 10.04. Now I have serious problems at startup: iscsitarget and heartbeat scripts do not start all the times I reboot. 
I have installed monit to try to start iscsitarget and heartbeat and guess what? It does not start too at boot.

In one of the two server sometimes it also starts with ethernet cards swapped.

Please tell me how to use old startup .

Thanks,

Mario

---

### Post by cdenley on 2010-05-17
I'm assuming they bind to a specific network interface, and fail if that interface is not up? Do they bind to the same one?

---

### Post by n43jl on 2011-08-09
I have the same problem. ubuntu desktop 10.10, 2.6.35-22-generic i686 GNU/Linux.
Heartbeat doesn't start and nothing is written to syslog. 
I created script /etc/init.d/heartbeat_autostart with:
```
service heartbeat start
```
and added it to rc.d, after that it began starting, but on one machine it sometimes tried to start before ethernet.
Adding on that machine heartbeat with priority level 99 seemed to resolve the problem:
```
update-rc.d heartbeat_autostart defaults 99
```
But on the other machine it works only with:
```
update-rc.d heartbeat_autostart defaults
```
If I try specify level 99, heartbeat_autostart doesn't start and writes nothing to log. 
So it seems to work, but looks very weak. And I can't find roots of the problems.

---

### Post by n43jl on 2011-12-16
May be [this]("https://bugs.launchpad.net/ubuntu/+source/heartbeat/+bug/494495")

---

