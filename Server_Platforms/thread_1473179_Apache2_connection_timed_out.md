---
title: "Apache2 connection timed out"
date: 2010-05-04
forum: Server Platforms
---

### Post by lovercjs on 2010-05-04
Hi,  I running Ubuntu Server 10.04_64. I had apache2 and tomcat6 running on the same server link via mod_jk. My network is behind a router and http (80) had been forward according. But when I try to access the apache2 from outside, it return a connection timed out. and ufw is disabled.  Anyone had any idea how to solve this? My router working fine, as I have another tomcat running on WinXP which is able to communicate with the outside.

---

### Post by lovercjs on 2010-05-05
solved! it's the anti-virus sitting on the win7 machine where the vmware sits. thanks for everyone who helped.

---

