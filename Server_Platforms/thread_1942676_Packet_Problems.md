---
title: "Packet Problems?"
date: 2012-03-18
forum: Server Platforms
---

### Post by jcook818 on 2012-03-18
Hello,

I have just set up Ubuntu Server on a VM machine to act as a router on my network. One of its network interfaces is connected to the modem using PPPoE, and it is routing to another interface connected to a wireless access point which is in turn serving my local network. While using a client connected to this network, everything seems to go well with the internet connection. However I've noticed that downloading a podcast from iTunes (i.e. a file of more than ~20mb) generates a 9006 error. Apple says "Your default packet size being set incorrectly can cause this error." I have no idea what to look for in my Ubuntu Server setup that can help me address this problem, which appears to be the Ubuntu Server not adjusted to accept packets of a certain size, and I could download whatever I wanted with my old router without issues... I have looked up what I can, my MTU is at the same level as my old router, etc. Does anyone know what might be causing this issue?

I am using iptables to do the routing as specified here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Thank you!

---

