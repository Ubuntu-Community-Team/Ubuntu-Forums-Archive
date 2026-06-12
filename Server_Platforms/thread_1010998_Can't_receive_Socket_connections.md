---
title: "Can't receive Socket connections"
date: 2008-12-14
forum: Server Platforms
---

### Post by cRaZyFaCKa on 2008-12-14
Hi,

Perhaps you guys know this right away :)
I've created several virtual machines with Ubuntu Server installations on them. I'm assigning to them ip's from my router so that I am able to communicate with them from other machines on my network.

The problem I am having, it's that those virtual machines won't receive/accept any kind of connections. I've installed Windows XP on one VM hoping to figure out whether this was a problem of the VMWare software I was using or not. It turned out that the XP installation did accepted all the connections I made into it, therefore, the problem seems to come from the Ubuntu Server itself.

I installed the VMWare tools on all of the installations, and further removed iptables and ufw (still without success).

I'm running the services in root mode.

Thank you for your attention :)

---

### Post by cRaZyFaCKa on 2008-12-16
I've realized that the problem seems to persist only when using Java RMI Registry. The clients cannot establish connections to the registry... :confused:

---

### Post by cRaZyFaCKa on 2008-12-16
Problem solved. There seemed to be a problem with my "hosts" file in /etc/hosts

Just commented the line with the 127.0.1.1

```
127.0.0.1	localhost
#127.0.1.1	cfk-lab

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

