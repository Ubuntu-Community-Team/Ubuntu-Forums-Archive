---
title: "turning off dhcp services"
date: 2008-03-19
forum: Server Platforms
---

### Post by HW_Hack on 2008-03-19
As a tech support person at a large high school - I'm requesting an ok from district IT to setup a Linux server ... bottom line is I'm requesting a static IP be assigned. And of course in any production environment I know you just don't want to hand out IPs / have servers setup.

At the same time I'm planning on being re-buffed + exasperated by a fearful IT dept (even though they run many Linux servers at the central office). If I was setting up a MS server (less secure - costs $$ - etc) I would already have the IP address in hand.

I'm setting up Ubuntu server with either an x-window or flux-box GUI. 

**Is there a setting / control where I can ensure the server will not act as a DHCP server and hand out IPs ?  This of course would be a bad thing ... **and something I forgot to set when I had to rebuild our Win2k server from scratch. DOH !!

Its primary purpose in life will to be a server students can test web SW on and practice ftp'ing files to.

---

### Post by Koybe on 2008-03-19
What you should do in this case, is a getting a fixed address from your dhcp server based on the MAC Address.

You'll find an example here : [http://www.brennan.id.au/10-DHCP_Server.html#setfixed](http://www.brennan.id.au/10-DHCP_Server.html#setfixed)

---

### Post by netztier on 2008-03-19
> **HW_Hack said:**
> 

**Is there a setting / control where I can ensure the server will not act as a DHCP server and hand out IPs ?  This of course would be a bad thing ... **and something I forgot to set when I had to rebuild our Win2k server from scratch. DOH !!


No worries. A basic installation of Ubuntu server has none of these services (DNS, DHCP, routing, Internet connection sharing etc) enabled by default - they're not even installed. 

After installation, it's just a computer that sits there. If you didn't choose a special installation option (such as the LAMP server), it won't do anything at all unless you start installing & configuring additional software packages, such as Apache, BIND, MySQL, DHCP etc. 

regards

Marc

---

