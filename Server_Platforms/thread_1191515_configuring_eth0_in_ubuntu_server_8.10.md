---
title: "configuring eth0 in ubuntu server 8.10"
date: 2009-06-19
forum: Server Platforms
---

### Post by mahendrakariya on 2009-06-19
can anyone tell me how can i configure eth0 on server edition. when i try "ifdown eth0" i get the mssg, "interface eth0 not configured"

---

### Post by mthalis on 2009-06-19
Go "sudo vi /etc/network/interfaces" and change what you want and restart network 
"sudo /etc/init.d/networking restart"

---

