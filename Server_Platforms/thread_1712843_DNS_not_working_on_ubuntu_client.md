---
title: "DNS not working on ubuntu client"
date: 2011-03-23
forum: Server Platforms
---

### Post by fizalhaq on 2011-03-23
please help me :(. I have success install DNS server using BIND on Debian 6.0. and it's work with windows client. but with ubuntu I can't ping all my domain. but if I use nslookup or dig from my ubuntu client, it's work. and I try connecting my ubuntu client to internet using modem. I don't get the problem. sorry if my english is not good.

---

### Post by jmacgowan on 2011-03-24
If everything is working as expected except for pinging your server, my guess is that your firewall is set up to drop ping requests.  I would start with checking your firewall rules.

---

### Post by fizalhaq on 2011-03-25
I can ping using IP but I can't using domain.

---

