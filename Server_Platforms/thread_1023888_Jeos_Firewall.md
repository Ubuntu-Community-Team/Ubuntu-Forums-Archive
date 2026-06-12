---
title: "Jeos Firewall"
date: 2008-12-28
forum: Server Platforms
---

### Post by nsolop on 2008-12-28
Hi everyone,

My name is Nicolas Solop from Buenos Aires Argentina. This is my first post here and is related to the installation of a firewall within a jeos server running on a VMware virtual machine.

Based on your experience which will be the best option to install a small firewall for a web server that will accept connections on the tcp 80 port and will make queries to a mysql database running on another server?.

Thanks for your time.

Regards,

Nicolas Solop

---

### Post by Drezard on 2008-12-28
Look into either ufw (google it) or have a look at iptables.

ufw is good for people just starting out with firewalls though.

Daniel

---

