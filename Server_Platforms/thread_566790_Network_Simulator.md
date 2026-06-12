---
title: "Network Simulator"
date: 2007-10-03
forum: Server Platforms
---

### Post by Epyonx on 2007-10-03
This is not directly related to Ubuntu but what is a nice (free) network simulator for Ubuntu/Linux or even Windows. For me to learn about servers and security I need to understand networks better.

Thanks in Advance

BTW Does anyone find Ubuntu Server a good learning platform for networking or should I stick to RHEL.

---

### Post by peabody on 2007-10-03
Any Linux distro is a good learning tool for networks, the distribution doesn't matter much, the network tools are the same on each distro (ifconfig, route, ip, etc, etc).  Only thing that's different are the startup scripts and configuration.  Debian based distros use /etc/network/interfaces for configuring networking, RHEL uses files under /etc/sysconfig I believe.

As for simulation, that's a good question, I'm not too sure.  I'm taking a networking class myself this quarter at my University.  I'd be interested to know as well.

---

### Post by netlogic on 2007-10-03
If you have enough ram, Virtual Machine is a way to go. Focus on designing many CLI based Linux machines. Give one of them with two nics. You can bridge them and route them and try many scenarios as you like. You probably want one bloated Linux distro that runs many services and build yourself a minimal Linux VM that requires only 32megs of less. Install many of them and only install minimal networking apps to test the connectivity and services. Create yourself a minimal scenario. You can also use a tool like nlite to make Xp memory requirement less.

---

### Post by Epyonx on 2007-10-03
What do you call enough ram ?

Im  going to try this tonight..

---

### Post by netlogic on 2007-10-04
I am running with 1.5gigs of ram. You might not need that much.
These are estimation.
256 for ubuntu using fluxbox as window manager with vmware server
32 to 64 megs for basic install with only running sshd as a service
196 xp made from using nlite
64 megs for virtual router (if you want to try a very simple router/firewall)
so on...
it all depends on what is your end goal. VM is the fastest way to learn basic networking using one box.

---

