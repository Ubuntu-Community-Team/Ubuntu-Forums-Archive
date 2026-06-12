---
title: "cant lookup hosts, ping, or apt-get"
date: 2009-08-26
forum: Server Platforms
---

### Post by lego12 on 2009-08-26
i cant ping any machine or website, exim doesnt work because it cant look up any hosts, and apt-get says fails to fetch
in ping it says unkown host: google.com
i have a static ip and in dmesg it says eth0: no ipv6 routers present
this all starts to happen after i fixed mysql by changing the bind-address
i also have iptables setup to accept ssh, www, mysql, https, webmin, and ftp

you can connect to the server but the server cant connect to you
this may be unrelated but lately ssh (in putty) it takes a long time to login and for it to ask my for my sudo password

---

### Post by jocampo on 2009-08-26
> **lego12 said:**
> i cant ping any machine or website, exim doesnt work because it cant look up any hosts, and apt-get says fails to fetch
in ping it says unkown host: google.com
i have a static ip and in dmesg it says eth0: no ipv6 routers present
this all starts to happen after i fixed mysql by changing the bind-address
i also have iptables setup to accept ssh, www, mysql, https, webmin, and ftp

you can connect to the server but the server cant connect to you
this may be unrelated but lately ssh (in putty) it takes a long time to login and for it to ask my for my sudo password

Run these two commands, please and show the results: route and ifconfig

I'm afraid you have a DNS issue and maybe your gateway is not configured. Try to ping a public IP. If you can post this message is because you are using a different machine I guess; get the IP for google, hotmail or whatever and put that in the browser and see what happen...

Edit: check if a firewall is blocking your internet access...

---

### Post by lego12 on 2009-08-27
im going to look at the routers dns settings i dont think it was setup properly last time i checked and then ill check the router firewall again

---

