---
title: "Get internet from another router?"
date: 2011-02-11
forum: Server Platforms
---

### Post by freshmeat20 on 2011-02-11
I have two routers in the same apt. building and just need to extend the wifi so the whole building can use. Using a netgear router (router x) as the secondary router without WAN how can I get internet from router y? What values should I put where in the NETGEAR config?

---

### Post by YesWeCan on 2011-02-11
I don't understand your question. Would you elaborate?

---

### Post by freshmeat20 on 2011-02-11
Im trying to use a second router which can reach the first router better to expand the reach of the wifi for people using laptops etc. Im using a NETGEAR to connect to a ACTIONTEC. I want to the second router (NETGEAR) to get it's Internet from the ACTIONTEC router.

---

### Post by iissmart on 2011-02-11
I don't think this has anything to do with Servers, nor Ubuntu in general. You just need to set up the Netgear router to act as a wireless bridge.

---

### Post by sanderj on 2011-02-11
> **iissmart said:**
> 
You just need to set up the Netgear router to act as a wireless bridge.

Indeed. In ASCII-art:

```
Internet ---- ACTIONTEC (with DHCP-server, with Wifi ) ---ethernetcable--- NETGEAR (**no** DHCP-server, with Wifi)
```

---

### Post by elico on 2011-02-12
not every router support this option that called WDS.
it's prefered to use access point or a router that has the support for access point usage such as in edimax routers.

---

### Post by cariboo on 2011-02-12
I have basically the same setup here, the wireless signal from my linkysy WRT310N is to weak to use in my shop, So I use an old SMC Barricade router. I have the two connected via an ethernet cable, then disabled DHCP on the SMC, and gave it a static ip address. I gave them both a different SSID, so I know which one I'm connecting to.

---

### Post by slimjim1520 on 2011-02-12
I have setup a similar setup with 3 access points. I had an extrenal dhcp server and disabled the dhcp service on the router itself so the clients used the dhcp server. With this setup i was able to use the same ssid with no problem.

---

