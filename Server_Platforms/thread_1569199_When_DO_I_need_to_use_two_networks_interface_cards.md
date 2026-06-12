---
title: "When DO I need to use two networks interface cards?"
date: 2010-09-06
forum: Server Platforms
---

### Post by dalitso on 2010-09-06
Please help me understand the difference between running a server with one nic and a server with 2 nics.

in a setup where a server with one nic (eth0) is connected to an ADSL router and all other PCs are also connected to the same ADSL router.
The server is running VPN, Samba/NFS, Postfix/IMAP, SSH and webmin., and ports 22, 1724, 10000(webmin) and 143 are open on the ADSL router.

Is it safe to run the above mentioned services with one nic?
Do i still need to setup firewall?

Is it better off to have two nics and set the other one to connect to my LAN and have a firewall block access to all ports on the external nic but the ones i need, and all access to LAN ?

When do I need two nics?

---

### Post by cj.surrusco on 2010-09-06
No, you don't need two NICs. Your router has a firewall. Just make sure that all of the opened ports are forwarded to your server's IP.

---

### Post by sikander3786 on 2010-09-06
+1 for firewall. Until you have a firewall in between your network and the internet, it should be safe enough.

---

### Post by dalitso on 2010-09-06
Thank you cj.surrusco and sikander3786.
So I guess I only need a second NIC if I want to run a DHCP server, right?

---

### Post by cj.surrusco on 2010-09-06
> **dalitso said:**
> Thank you cj.surrusco and sikander3786.
So I guess I only need a second NIC if I want to run a DHCP server, right?

Yeah, that would be pretty much the only reason, but your router probably has a DHCP server built-in, if it is fairly new. Another reason you may want a second NIC would be if the server was connected directly to the internet, and you could connect the other computers to the second NIC, and only have to configure the firewall on the server. But again, your router probably has a firewall, so you wouldn't need to worry about that.

---

### Post by dalitso on 2010-09-06
Thank you again.
Yes, the router has a firewall and dhcp server. Its just that most people this side like to use two NICs and also server iptables, yet the router has both. Maybe they just don't trust the router or they just like setting up iptables and their own DHCP server.

---

