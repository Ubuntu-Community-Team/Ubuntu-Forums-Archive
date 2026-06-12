---
title: "unable to relay internet to lan from linux box"
date: 2009-06-21
forum: Server Platforms
---

### Post by pawan_lal on 2009-06-21
hello  friends,


i  had  configured  vpn on my linux box OS is fedora 7, having two NIC

eth1 - 192.168.1.103 its D/G is 192.168.1.254 (ip of adsl router)
so  my  eth1  is  directly  connected  to  adsl

eth0 - 192.168.2.107  its D/G is 192.168.1.103(confused here what will be the D/G of eth0)
so here eth1 is connected  to  switch

n  did  ip  forwarding in /etc/sysctl.conf

net.ipv4.ip_forward = 1


now  at  client  side  gave  ip  to  my  window client 
ip      192.168.2.22
S/M  -/24
D/g   - 192.168.2.107

now i think client should get access of the internet but they r not able to get.
plz guide me where i am doing mistake.

tx

---

### Post by evermooingcow on 2009-06-21
I don't think eth0 should have a default gateway.
 
 Can you clarify "no access to internet"?
 - Does ping work from client to internet?
- Does name resolution work?
 - Can you connect to an external site via ssh?
 - What do you see when you try to load a web page from the client? Does it error right away or try to load and show a blank page for a long time?
 
Have you restarted the network service to reflect the ip forwarding setting?

 Could you post the routing table? Maybe it will help.
  ```
/sbin/route -n
```

---

### Post by Bachstelze on 2009-06-21
> **pawan_lal said:**
> 
n  did  ip  forwarding in /etc/sysctl.conf

net.ipv4.ip_forward = 1


That's not enough. You have to also setup the actual packet forwarding using iptables. [Here](http://www.gentoo.org/doc/en/home-router-howto.xml)'s a guide about how to do it.

---

### Post by ssffzzxx on 2009-06-22
Hello , 
I think, maybe you forget to configure NAT
If you want to share the connection, and you want to use the linux box as gateway for internet, you should configure NAT.

tldp.org/HOWTO/Home-Network-mini-HOWTO-3.html 

Hope this help.
Best Regards

---

