---
title: "If linux is low on resources..."
date: 2008-03-17
forum: Security Discussions
---

### Post by CoffeeBreath on 2008-03-17
why set up a firewall on it's own machine and why should a print server have it's own machine?

---

### Post by stalker145 on 2008-03-17
> **CoffeeBreath said:**
> why set up a firewall on it's own machine and why should a print server have it's own machine?

From an amateur's (mine) point of view, one would want to run a firewall on its own machine so that there are not multiple points of entry (weaknesses) in the system. If you have a web server running along side your network's firewall, it's another possible way for the baddies to get in.

As for why a print server should be by itself... I see no reason. I have a standard desktop running with a print server on it.

---

### Post by p_quarles on 2008-03-17
> **stalker145 said:**
> From an amateur's (mine) point of view, one would want to run a firewall on its own machine so that there are not multiple points of entry (weaknesses) in the system. If you have a web server running along side your network's firewall, it's another possible way for the baddies to get in.

As for why a print server should be by itself... I see no reason. I have a standard desktop running with a print server on it.
+1.

A separate hardware firewall is pretty much the de facto standard for home networks, regardless of the OS you are using. Most people don't even really think about this, as they use a separate NAT router that provides the hardware firewall functionality. Most such routers run some sort variation on *nix. 

In any case, building your own hardware firewall would require an extremely low end computer. Filtering network traffic does not require much in the way of computing resources.

---

### Post by Lord Illidan on 2008-03-17
The way I see it, if you want to use a dedicated machine for a firewall, you want as few vulnerabilities as possible, thus it wouldn't have any desktop elements. In Unix, the philosophy is 1 program - 1 task. This is extended to the real world. 1 machine - 1 task. A cheap Linux machine can act as a perfectly good firewall. The same goes for a print server. Of course, a large network has more need for a print server than a home network or a single desktop.

Linux can run a firewall and a print server and even a desktop all at once, but such a system violates the Unix principle, and creates vulnerabilities.

---

### Post by CoffeeBreath on 2008-03-18
Thanks for the help folks.

---

