---
title: "Trying to run Kismet"
date: 2007-11-13
forum: Server Platforms
---

### Post by diec23 on 2007-11-13
I get this output when I run it.  I assume this means it is unable to set my wireless card into monitor mode?  is there some way to enable that?

[CODE]Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (Wireless Card): Enabling monitor mode for ipw3945 source interface eth0 channel 6...
FATAL: channel get ioctl failed 95:Operation not supported
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
[CODE]

---

### Post by wieman01 on 2007-11-13
It needs to support packet reinjection... so you should look for an IPW3945 driver patch that enables it.

---

