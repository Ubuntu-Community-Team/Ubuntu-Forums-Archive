---
title: "Finding my routers IP for my LAN"
date: 2006-08-10
forum: Server Platforms
---

### Post by cobbweb on 2006-08-10
Hey, 
  I'm at college and living in housing that has me linked to the internet via "their" router. I set up a proxy and discovered what port they use to connect to my computer. This means I can basicly do one thing with my server, and since im just using it as a proxy, it works out just fine. However, I don't know the IP of the router they are using. Is there anyway to find out what the IP of it would be? So I can configure my squid proxy? Thanks, 

 Cobbweb

---

### Post by The Uniphobiac on 2006-08-10
Routers have multiple IP addresses, dpending on how they are setup...you probably do not have access to the router by IP anyhow.  To connect to your server, your need you IP address, not the routers IP.  You can use trace route to discover your gateway IP.

---

