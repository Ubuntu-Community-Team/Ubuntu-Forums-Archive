---
title: "Discrepancy between ifconfig and /etc/network/interfaces"
date: 2008-12-16
forum: Server Platforms
---

### Post by SgtBeano on 2008-12-16
I hope someone can help me here, I have a wired problem on 8.10 server with Gnome (I know).

ifconfig returns that eth0 is on 10.11.2.94 which is dynamic and I want it to run on a static IP which I've specified in /etc/network/interfaces but it won't work.  The funny thing is, it has been working fine and after a reboot, the network manager applet had a cross on it and couldn't detect my nic anymore - it is there and working becuase I can connect on 10.11.2.94?

---

### Post by albinootje on 2008-12-16
> **SgtBeano said:**
> I hope someone can help me here, I have a wired problem on 8.10 server with Gnome (I know).

ifconfig returns that eth0 is on 10.11.2.94 which is dynamic and I want it to run on a static IP which I've specified in /etc/network/interfaces but it won't work.  The funny thing is, it has been working fine and after a reboot, the network manager applet had a cross on it and couldn't detect my nic anymore - it is there and working becuase I can connect on 10.11.2.94?

If i need a static ip on some machine for permanent or for a while i prefer removing network-manager and use /etc/network/interfaces.

Network-manager is cool to have in general, but sometimes i find it very annoying when i quickly want to work with a customized /etc/network/interfaces 
I've seen Network-manager filling logs with info even when i turned "connection" off in Network-manager itself.

---

### Post by iponeverything on 2008-12-16
network manager ignores devices configured via the interfaces file.

Or least it is suppose to (it has always done it correctly with me)

post your interfaces file, maybe there is an issue it.

---

