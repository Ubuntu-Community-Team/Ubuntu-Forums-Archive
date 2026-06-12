---
title: "Hostname"
date: 2005-08-17
forum: Server Platforms
---

### Post by SychoSly on 2005-08-17
How do I change the host name on my system? I have the server install.

---

### Post by grj on 2005-08-17
Take a look at 

man hostname

I think it will tell you what you need.

---

### Post by LordHunter317 on 2005-08-18
edit /etc/hostname, use hostname to set it on the running system, update /etc/hosts if necessary, restart any running daemons that care.

---

