---
title: "DNS oddity"
date: 2014-02-22
forum: Server Platforms
---

### Post by david_brown on 2014-02-22
I'm running Ubunbtu 12.04 on my home server and am having troubles with apt-get update amongst others. I have found out that if I add 

nameserver 8.8.8.8
nameserver 8.8.4.4

to /etc/resolv.conf after booting the server I get no problems whilst it's running. Obviously this need to be done on each boot. Is there somewhere I need to add these lines so that it's done automatically on boot?

Thanks

---

### Post by SeijiSensei on 2014-02-22
You can add them to /etc/resolvconf/resolv.conf.d/head, which is used to generate /etc/resolv.conf upon boot.  That said, resolvconf should be able to figure out what your DNS servers are during DHCP negotiation.  If you look in your router's configuration, you should see a place where you can put the addresses of the Google servers and have them distributed automatically to your workstations during the address-negotiation process.

---

