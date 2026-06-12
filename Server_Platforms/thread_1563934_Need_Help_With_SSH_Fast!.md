---
title: "Need Help With SSH Fast!"
date: 2010-08-29
forum: Server Platforms
---

### Post by belmont52 on 2010-08-29
Hello,

i have recently set up anew ubuntu server and i cant ssh into it from the internet, i can ssh from local network with no problems but when i enter my public ip it comes back saying "could not resolve hostname my.public.ip.addy: name or service not known" please help! thank you
Belmont

---

### Post by belmont52 on 2010-08-29
anyone?

---

### Post by AlphaLexman on 2010-08-29
Do you have a firewall? you will have to configure the firewall to get past it, otherwise anyone could get to your system!

---

### Post by belmont52 on 2010-08-29
yes but i configured port forwarding for 22 to forward to my server

---

### Post by BkkBonanza on 2010-08-29
> **belmont52 said:**
> could not resolve hostname my.public.ip.addy: name or service not known

This error message indicates that you have a DNS lookup problem. Verify that you have setup the name correctly. It has to resolve the name before it even tries to get to your router so at this point the router and forwarding is not the issue. 

Use **nslookup** or **dig** to check the name and determine why it is not resolving. dig can give more info but it is not installed by default - you would need the dnsutils package installed (**sudo apt-get install dnsutils**).

---

