---
title: "Authentication rules for SSH"
date: 2008-10-12
forum: Server Platforms
---

### Post by lykwydchykyn on 2008-10-12
I have a question about ssh authentication rules.  I have a server that I'm exposing to the internet so I can ssh in from outside.  I would like it so that I can use ssh with a password on the local network, but that key-based authentication is required for connections outside the LAN.  

Anyone know if this is possible?

---

### Post by iponeverything on 2008-10-12
My guess is that you will have to setup two ssh servers running on different ports and interfaces, using different configuration files.  You can setup port redirection on your external interface so that from the outside ssh will not appear to be on a non-standard port.

---

