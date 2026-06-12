---
title: "Firewall blocking my Mom"
date: 2006-11-15
forum: Server Platforms
---

### Post by GameboyHippo on 2006-11-15
I'm experiencing some unusual behavior.  I'm running apache2.  I have a personal website that has things like baby pictures, etc... on it.  Unfortunately, when my mother attempts to connect to my site from her home network, it times out.  I get a log in firestarter telling me that the connection was dropped.  So I right clicked and clicked the option to allow service from the source.  In fact, everybody can access port 80 to view my site.  Any other machine can connect except machine's from Mom's IP.  I can't find any configuration for firestarter that denies access to the port.  I grepped through /etc for her IP address and here's my results:

cd /etc
grep -R "mom's ip" *
firestarter/inbound/allow-from:mom's reverse dns, 
firestarter/inbound/allow-from:mom's ip, 
firestarter/inbound/allow-service:HTTP, 80, mom's reverse dns, 
firestarter/inbound/allow-service:HTTP, 80, mom's ip, 

Any suggestions?

---

### Post by GameboyHippo on 2006-11-15
I think I found something.  I did an iptables --list command and I saw this:

REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

I ping mom's email address and received no response.  So could this rule be rejecting the connection?  If so, what do I have to change to allow her computer to connect?

---

