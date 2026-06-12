---
title: "Help needed"
date: 2006-01-18
forum: Server Platforms
---

### Post by Nixforce on 2006-01-18
Hi ..

In 3 to 4 weeks my ADSL line is being installed and i woiuld like to setup Ubuntu as a gateway server, with apache, mysql, and dynamic dns to manage the dns server, I would like the server to act as a gateway for 2 other pc's on the local network... Are there any guides to get this done?

---

### Post by tomski on 2006-01-18
ask the isp to provide a router (1port) setup/configured in 'NO-NAT' mode
put 2 networkcards in the server eth0 = WAN (untrusted), eth1 = LAN (trusted
then connect a hub or switch to eth1

this setup may be pricy but you will have more control over the traffic & you could always use a modem insted of a router

---

