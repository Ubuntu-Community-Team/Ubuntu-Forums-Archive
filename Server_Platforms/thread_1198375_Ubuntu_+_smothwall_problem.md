---
title: "Ubuntu + smothwall problem"
date: 2009-06-27
forum: Server Platforms
---

### Post by pardi_krk on 2009-06-27
HI,
I've set up Ubuntu server as router with 2 NIC
(In order to the part of this tutorial: [http://howtoforge.com/ubuntu6.06_firewall_gateway]("http://howtoforge.com/ubuntu6.06_firewall_gateway")) 

    eth0 192.168.1.100
    eth1 192.168.1.110

eth0 -  connected to net(router 192.168.1.1)
eth1 -  local lan (switch + some PC's)

Problem is that I can't connect even with router.
I can ping both NIC from every machines, I can connect with putty to both interfaces. From server I can't ping my router. But, if I down eth1 itherface then eth0 can connect with router and wan, of course other local machines lost connection with a server. Even if I will up eth1 back local machines can't find server. However, I tracered packages and it looks like eth0 doesn't know where is 192.168.1.1.... 

Any idea, any help? 

Thanks a lot.

---

### Post by kustomjs on 2009-06-27
sorry but your title is misleading.

are you using smoothwall as your router?
or 
are you using ubuntu as your router?

smoothwall is different then what ubuntu is.

because I have smoothwall as my router and I got 3 servers behind of the smoothwall and they are working great so we need to know what your using.

---

### Post by pardi_krk on 2009-06-28
HI,
I've installed  Ubuntu as server (samba+squid) and install smothwall as firewall. So in this case smotwall is my "router"...

P

---

