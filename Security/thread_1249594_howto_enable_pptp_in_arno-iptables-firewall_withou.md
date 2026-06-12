---
title: "howto enable pptp in arno-iptables-firewall without NAT ?"
date: 2009-08-25
forum: Security
---

### Post by hanasaki on 2009-08-25
how can the dpk-reconfigure arno-iptables-firewall be setup to allow pptp incoming and outgoing without enabling NAT of all internal to external?
Thank you.

---

### Post by cariboo on 2009-08-25
You probably have to edit it by hand to turn NAT off. it 's been a while since I looked at it, but if you open the script in a text editor as root, search for NAT and set it to off.

---

