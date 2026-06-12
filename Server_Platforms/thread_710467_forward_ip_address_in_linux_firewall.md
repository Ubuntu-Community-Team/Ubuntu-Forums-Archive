---
title: "forward ip address in linux firewall"
date: 2008-02-28
forum: Server Platforms
---

### Post by tocleora on 2008-02-28
We are setting up nat in the linux firewall section of webmin.  We have it all working, but what we want to do now is if someone internally types in [internaladdress] it will automatically forward them to [externaladdress], so if they type in 196.168.100.100 it will automatically forward them to ubuntuforums.org for example.  Can someone tell me how to do that within webmin?  Thanks in advance.

---

### Post by k_grdn on 2008-02-28
Hi,

Types in address where?

To change source to dest addresses use SNAT but this will not work for external addresses that you don't own.

If you want to type in an address in a brower use apache redirects.

What exaclty do you wish to achieve?

Regards,

k_grdn

---

### Post by tocleora on 2008-02-28
we're on one network that the servers are internal on right now and we're moving a group of people to another network those servers wont' be internal on anymore, so we need these people to use the external address instead until we can move these servers over to the new network.  We don't want them to bookmark and/or get used to using the external address because once we change it we'll want them to go internal again, so we thought it would be better just to put something somewhere that would automatically forward any request to the internal ip to the external ip.  and yes they are web servers but they won't hit apache using an internal ip so we can't use apache to forward.  

How do company's do it to where if you type in [www.[explicative].com](www.[explicative].com) it sends them to an internal page?  I would think that method would work similar for us...

---

### Post by farruinn on 2008-02-28
> **tocleora said:**
> How do company's do it to where if you type in [www.[explicative].com](www.[explicative].com) it sends them to an internal page?  I would think that method would work similar for us...

Probably running their own, local DNS server? I assume people on the LAN can browse outside the LAN normally, so you shouldn't have to change the firewall.

---

### Post by cdenley on 2008-02-28
> How do company's do it to where if you type in [www.[explicative].com](www.[explicative].com) it sends them to an internal page?
To answer your question, I did something like this when I made a captive portal.
```

sudo iptables -A PREROUTING -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.5

```
This rule sends all traffic coming in on port 80 to 192.168.0.5. However, if I understand correctly, instead of redirecting an external request back internally, you want the reverse. I don't think this would work because the web request wouldn't get routed, and nat rules wouldn't apply. You can set up an apache server on your LAN specifically for redirection, then set up a simple redirection script, or configure mod_proxy.

---

