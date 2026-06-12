---
title: "virtual hosts from LAN"
date: 2006-01-30
forum: Server Platforms
---

### Post by franke on 2006-01-30
my server is behind my router, which is connected through a connection with dhcp. I have one external ip, and several virtual hosts on the server. 
They work fine from the outside, but when I try to reach the hostnames from the LAN the lead me to the router. 
I have tried a lot of different stuff on the apache-files, virtualhosts, etc.

Can I do anything else on the system ?

---

### Post by Horndog on 2006-01-30
Some routers can't do "Internet loop back". In my case I switched the MAC address to my ISP from a computer to my router and I was able to have "Internet loop back". YMMV

---

### Post by franke on 2006-01-31
I dont think that's it... I had the exact same setup a couple of days ago. I changed my server to another computer and installed ubuntu on it. 
I never had any problems reaching my hostnames from the LAN.

Before I had freeBSD, with apache1.3.

---

