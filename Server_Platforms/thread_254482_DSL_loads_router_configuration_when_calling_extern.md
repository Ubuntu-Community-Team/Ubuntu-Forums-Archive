---
title: "DSL loads router configuration when calling external IP"
date: 2006-09-10
forum: Server Platforms
---

### Post by papayiya on 2006-09-10
Hi,

I'm in the process of switching over from Cable internet to DSL. I have an ubuntu server already set up. I've done the switch with the internet and the server has an internet connection now.

The problem is, if I go to my website from FireFox (say [www.xyz.com](www.xyz.com)) the router loads the adminitrstation console for my router. If someone outside of my network tries the same website, it works fine. I guess the router resolves my IP address, sees I'm coming from within the network and loads the routers gatway (192.168.2.1)?

Here is my routing table:

Destination Netmask Business Internet Gateway Flags Metric Interface
127.0.0.0 255.0.0.0 127.0.0.1 1 lo0
192.168.2.0 255.255.255.0 192.168.2.1 1 LAN
70.52.xxx.xx 255.255.255.255 70.52.xxx.xx 1 PPPoE 0/35
Default Gateway - 64.230.199.5 5 PPPoE 0/35

If anyone has an idea whats going on, please let me know.

Thanks
papayiya

---

### Post by chrisfay on 2006-09-10
If your router has the option to change which port its web-utility works on you could do that.I beleive your router would no longer direct internal requests on port 80 to the router utility. 

You alternatively can add an entry into /etc/hosts for your domain and LAN IP of your server. That would keep requests from routing to 192.168.1.1(gateway). Something like:

192.168.1.10  my.domain.name

There's probably other ways around that, but just some ideas.

---

### Post by papayiya on 2006-09-12
Thanks  

I did this, it worked.

All the best

---

