---
title: "Firestarter not closing ports"
date: 2007-09-12
forum: Server Platforms
---

### Post by TonyLechner on 2007-09-12
I am running Firestarter as my firewall, and have only opened a few ports, but upon a quick portscan of my machine, I found three ports open that are not allowed by the firewall policy.

I'm a newly converted, just installed Ubuntu yesterday, but would anyone have any idea as to why this is and, more importantly, how I can close these ports if my firewall is not doing it?

(I'm running tor and privoxy, if that helps, but it isn't any of their default ports)

---

### Post by steve.horsley on 2007-09-12
Were you scanning the machine from itself? Normally, the PC is allowed full access to its own ports.

If you can make sense of it, the command
**sudo iptables -L**
will list all the rules that are currently in force.

---

### Post by digen on 2007-09-12
I would also suggest scanning the machine from outside the network or from a different computer within the same network to get a broad and clear picture.

---

