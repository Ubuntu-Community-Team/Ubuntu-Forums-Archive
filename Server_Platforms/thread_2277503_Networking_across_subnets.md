---
title: "Networking across subnets"
date: 2015-05-09
forum: Server Platforms
---

### Post by scojopa on 2015-05-09
I have a few ubuntu 12 servers running on a switch. I can ping the servers from the switch itself. 

But for devices that come over the firewall (Wireless) I cannot ping or access the servers. I have not trouble pinging and accessing all other devices on the same switch - just the ubuntu servers. 

Switch, Ubuntu Servers, SAN all on the same class c network
Wireless is on a different class C network

Why can I access all other devices on the switch except ubuntu servers? 

Thanks
Scopa

---

### Post by tgalati4 on 2015-05-09
A diagram of the network would be helpful.  Can any of the servers ping any of the wireless devices?  I presume that you have static IP's set up on the servers and you have correctly set up /etc/network/interfaces for each machine.  I also presume that you have set up the [DNS resolver]("http://askubuntu.com/questions/157154/how-do-i-include-lines-in-resolv-conf-that-wont-get-lost-on-reboot") correctly.  If you turn off the firewall on the wireless router, can the wireless devices access the servers?

---

### Post by volkswagner on 2015-05-09
Please post your /etc/network/interfaces file and as tgalati4 suggests the network diagram.

Can servers ping other servers?

On servers post output of:

```
route
```

You say you can access other devices connected to switch via wireless, does this include ping?

From wireless device you can do traceroute and route print, depending on OS.

---

