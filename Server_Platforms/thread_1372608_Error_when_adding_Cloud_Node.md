---
title: "Error when adding Cloud Node"
date: 2010-01-04
forum: Server Platforms
---

### Post by egeier on 2010-01-04
First time setting up Ubuntu Cloud system.

I get error during install when searching for and trying to add node from the Cloud Controler:
New node found on 192.168.1.182:add it? [Yn] y
Connecting to 127.0.0:8774...failed: Connection refused.
Error: you need to be on the CC host and the CC needs to be running.

Anyone have ideas? Thanks for your help!

---

### Post by munky99999 on 2010-01-04
127.0.0:8774

You're lacking a .1 at the end there for the proper loopback.

127.0.0.1:8774 will then allow the cloud controller to connect back to itself.

Connect to the cloud controller webpage using web browser. Login and change that so it's the full address.

---

### Post by egeier on 2010-01-04
Sorry for the typo, that's actually what it shows on the screen 127.0.0.1. Can you think of anything else? Thanks!

---

### Post by munky99999 on 2010-01-05
> **egeier said:**
> Sorry for the typo, that's actually what it shows on the screen 127.0.0.1. Can you think of anything else? Thanks!

Are you installing this on a system that already existed or did you go straight from cd?

Possibly you have say iptables enabled to block that port.

Other then that just need more info.

---

### Post by egeier on 2010-01-05
Installed from CD like at:
[http://help.ubuntu.com/community/UEC/CDInstall](http://help.ubuntu.com/community/UEC/CDInstall)

I didn't install IPtables and i just tried to stop the service and check its status and it errored...don't think its installed by default.

---

