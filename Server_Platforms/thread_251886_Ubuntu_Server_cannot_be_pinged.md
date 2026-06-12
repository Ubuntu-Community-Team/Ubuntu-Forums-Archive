---
title: "Ubuntu Server cannot be pinged"
date: 2006-09-06
forum: Server Platforms
---

### Post by dxt on 2006-09-06
Hi everyone.
Can someone please help me figure out why a freshly installed ubuntu 6.06.1 server cant be pinged given that it has a public ip?

I have not even done anything with it after the installation. I just wanted to check if it responds to "pings"

typing iptables -L shows no firewall rules set up.
does ubuntu server block icmp /ping by default right after install?

---

### Post by Uluen on 2006-09-06
What do you mean with "public IP", not in the 10x/172x/192x range? Is it behind a router/firewall? Ports forwarded to it?

---

### Post by dxt on 2006-09-06
not sitting behind any router at all. dsl internet comes in via a modem (gateway). From there it connects immediately to the PC running ubuntu 6.06.1 server. new install.

no port forwarding.
the server is at 202.163.202.186
[http://www.dnsstuff.com](http://www.dnsstuff.com) cant ping it as well

---

### Post by Uluen on 2006-09-06
Ok, all the DSL modems I've used also was a router.
DLS modem dial ISP and get public IP etc.

---

