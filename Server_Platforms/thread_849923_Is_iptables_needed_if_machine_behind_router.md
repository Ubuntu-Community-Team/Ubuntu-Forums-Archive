---
title: "Is iptables needed if machine behind router?"
date: 2008-07-05
forum: Server Platforms
---

### Post by skunkbad on 2008-07-05
I can see if I wanted to block certain IP addresses from accessing my machine, that customizing iptables would be beneficial. Is there any other reason why I would need to use iptables if I already have a router doing the port forwarding / packet dropping? My machine is not in the router's DMZ, in case that matters.

Also, I read somewhere on the main ubuntu site that the default install of Ubuntu Server Edition 8.04 has all ports blocked. Even without customizing iptables, wouldn't it theoretically be impossible to get hacked?

---

### Post by windependence on 2008-07-05
IMHO, a good hardware firewall is MUCH better than software any day of the week. I don't install a Linux firewall on any of my Linux boxes because of this.

-Tim

---

### Post by kevdog on 2008-07-05
You probably don't need iptables installed if the following conditions are met:
1. You trust the other computers on the LAN
2. You are not port forwarding any ports to a computer located on the LAN.  Even in this situation running iptables is debatable. 

By default all outgoing, incoming, forwarding rules are OPEN (not blocked) by default on installing Ubuntu -- no ports are closed.

---

### Post by skunkbad on 2008-07-05
> **kevdog said:**
> ... By default all outgoing, incoming, forwarding rules are OPEN (not blocked) by default on installing Ubuntu -- no ports are closed.

This is what Ubuntu says on [http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security"):
> 
[SIZE="3"][COLOR="Sienna"]No open ports[/COLOR][/SIZE]

By default, Ubuntu does not install default services that listen on open network ports. (The astute reader will note that local network service clients like DHCP and Avahi are the only exception.) This reduces the chances that a system would be compromised through a service that was installed without the explicit knowledge of the administrator.

So, maybe this is new for 8.04?

---

### Post by kevdog on 2008-07-05
Please read what you posted:

> By default, Ubuntu does not install default services that listen on open network ports

There are no default listening services, however there are open network ports.  I'm not trying to split hairs just point out the difference.  The difference however is illrelevant.  Having open ports with no listening services is not a security risk.  You need to have a program listening on a port and the port open to have a potential security risk.

---

### Post by skunkbad on 2008-07-05
OK, that makes sense. I didn't mean to sound like I was arguing. I'm just trying to learn, and need to ask questions (and probably need to think more about what I'm reading).

So, in regards to what you said earlier...

I have no worries about other users on the LAN, and I'm only forwarding ports through the router to this server. No other computer on the LAN has ports being forwarded to it. So, I'm assuming I'm more or less safe.

Thanks for the replies.

---

### Post by windependence on 2008-07-06
> **kevdog said:**
> 2. You are not port forwarding any ports to a computer located on the LAN.  Even in this situation running iptables is debatable. 


You don't actually need IPtables to forward ports from your router. One has nothing to do with the other.

-Tim

---

