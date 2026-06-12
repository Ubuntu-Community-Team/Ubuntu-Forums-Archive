---
title: "UFW and Steam"
date: 2012-05-28
forum: Security
---

### Post by valeno on 2012-05-28
I am having some trouble allowing steam over my UFW firewall. According to steampowered.com i have all the correct ports open but it still will not get past the updating screen when i start steam unless UFW is disabled.       udp 3478,4379,4380 outbound. udp 27000-27015, 27015-27030 allowed. tcp 27014-27050 allowed.

---

### Post by Ms. Daisy on 2012-05-28
I found for me the best way to determine which ports are needed is to open the service with ufw running, then look at the ufw logs to see exactly which ports and protocols are being blocked.  Then write a rule for those.  Don't forget to allow the source & destination ports.

---

