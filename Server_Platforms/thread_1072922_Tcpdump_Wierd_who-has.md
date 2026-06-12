---
title: "Tcpdump: Wierd who-has"
date: 2009-02-17
forum: Server Platforms
---

### Post by secondstage on 2009-02-17
I have a sever behind a router at my home, and have port forwarding setup for it. The internet connection slowed down allot today, so I decided to look at the tcpdump of the server, and I'll get messages like...
```
arp who-has 192.168.0.114 tell 192.168.0.1
```
Funny thing is that there isn't a computer at 192.168.0.114. The calls are constant, and might be slowing down the network. 

I use the server remotely (it is in the basement), and use ssh, and sshfs to work with it. If I turned of the machine before closing the connection, could ssh, or sshfs still be looking for the machine?

Please tell whether or not I am correct in my assumptions, or whether the problem maybe something else.

---

