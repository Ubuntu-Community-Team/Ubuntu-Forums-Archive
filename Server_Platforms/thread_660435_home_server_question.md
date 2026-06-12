---
title: "home server question"
date: 2008-01-06
forum: Server Platforms
---

### Post by fedex1993 on 2008-01-06
how could i change like the adres to my home server like so it can be publically broadcasted

---

### Post by invar9 on 2008-01-06
It depends on what you would like to do and you network setup. 
If you totally want to expose it to the internet, put it outside your router or in a DMZ zone. 
If you just want to run a specific service, just port forward the correct ports to the internal IP address.

---

### Post by HermanAB on 2008-01-06
First you would need to change your service plan with your ISP and get a so called 'server' account.  This typically costs about $10 more per month, but you will also get much higher bandwidth and they will then remove the blocks on ports 20, 21, 25 and 80 which they most likely have.  The ISP will allocate you at least two fixed IP addresses.

Then buy a domain name at Godaddy and configure the DNS to point to your IP addresses.  Finally, change your firewall so that the ports that you want to expose (22, 25, 110, 143, 80, 443 for example) are forwarded to your server.

Hope that helps!

Herman

---

### Post by elvinatom on 2008-01-07
$10 more for !2! static IP addresses + higher bandwidth ... now i don't know where you live or who your isp is but i pay more than twice for my (single) static account with identical bandwidth to consumer accounts.  I don't say you're lying, but please tell me, is that normal in you country?

---

### Post by orgrimdoom on 2008-01-07
where i am we pay 40$ a month and have 8 static IP's . . . . but we also only have 256 kb/s up and 1 meg down.

---

### Post by fedex1993 on 2008-01-07
well actually i get ulimited and i manage the ports on our router and i can open them enad close them. But like how could i get a web adress and what not

---

