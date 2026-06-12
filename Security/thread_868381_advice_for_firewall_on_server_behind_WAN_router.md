---
title: "advice for firewall on server behind WAN router"
date: 2008-07-23
forum: Security
---

### Post by JordanCB on 2008-07-23
Howdy!

I have a few questions for the security guru's out there.

I have a router that is my gateway out to the net.  This router has the built-in firewall on it and port forwarding, I am forwarding port 22 for remote ssh into a server on the LAN behind the router.  

I have created some firewall rules using iptables on an Ubuntu HH install.  I am servicing smtp and pop3 as well as samba.

Am I correct in assuming that if the firewall on the router is only forwarding ports 25, 110, and 22 to my LAN server, that I will 'theoretically' be safe behind the router? 

On my server on the LAN I am only allowing port 22 traffic to my server and 110 and 25 to my server.  Will samba still work okay? Do i need to open ports 137-139 udp and tcp on my server in order for the other LAN workstations to access my samba shares?

I'm just trying to secure my little network a little better than it already is.  Are there any security holes in default samba installations, or mail services that I should also check and defend against?  Just looking for some tips on this kind of network layout.  Any suggestions are greatly appreciated!!

Let me know what you guys suggest.

Thank you!

-- JCB

---

### Post by hyper_ch on 2008-07-24
> **JordanCB said:**
> Am I correct in assuming that if the firewall on the router is only forwarding ports 25, 110, and 22 to my LAN server, that I will 'theoretically' be safe behind the router?
Safe from?
you can be attacked on port 25, 110, 22 and all other ports if there's a flaw in the router. 

> **JordanCB said:**
> Are there any security holes in default samba installations, or mail services that I should also check and defend against?
Not that I know of any but what mail services do you use?

---

