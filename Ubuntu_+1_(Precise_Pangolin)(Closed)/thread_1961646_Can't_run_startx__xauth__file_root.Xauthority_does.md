---
title: "Can't run startx  xauth:  file /root/.Xauthority does not exist"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Kneegrowplease on 2012-04-19
```
pedro@pedro-ET1330:~$ sudo startx
[sudo] password for pedro: 
xauth:  file /root/.Xauthority does not exist


Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxinit: giving up
xinit: unable to connect to X server: Resource temporarily unavailable
xinit: server error
pedro@pedro-ET1330:~$ 

```

12.04
:confused::confused::confused:

---

### Post by CharlesA on 2012-04-19
Don't run startx as root.

In any case, an x server is already running.

---

### Post by Kneegrowplease on 2012-04-21
Solved,

---

