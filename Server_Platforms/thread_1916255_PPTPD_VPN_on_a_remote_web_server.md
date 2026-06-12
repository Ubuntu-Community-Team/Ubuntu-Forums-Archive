---
title: "PPTPD VPN on a remote web server"
date: 2012-01-27
forum: Server Platforms
---

### Post by oldskool on 2012-01-27
Currently i have a web server in the USA which is a bit of a testing box but does run a couple of web sites. Apache / MySQL etc.  

I use a proxy to give me access to U.S services that geo-locate normally, i'm in the UK.


Today i tried to install a VPN service, pptpd. All worked great but no internet access. 

Then i realised i had to masquerade the traffic so i followed this tutorial: [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

The ufw Masquerading config


Since doing this i lost all connection to the server, perhaps i niavely ignored the need to run this server as a web server using port 80, 22 etc... I assume enabling NAT forwarding between interfaces broke the external routing for my web and ssh traffic? 

Does anyone know what i need to do to enable the NAT forwarding for VPN net access and also keep it functioning as a server too. 


Thank you

---

