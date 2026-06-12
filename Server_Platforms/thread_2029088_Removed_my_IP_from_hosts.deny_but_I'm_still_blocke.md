---
title: "Removed my IP from hosts.deny but I'm still blocked"
date: 2012-07-19
forum: Server Platforms
---

### Post by clay7 on 2012-07-19
I was testing my server last night and ended up blocking myself. My IP was put into /etc/hosts.deny but I deleted that address and rebooted. However, I'm still blocked. What did I miss?

Other info: In fail2ban, it's set to ignore repeated requests from my IP address.

---

### Post by clay7 on 2012-07-19
Got it. To fix this:

> sudo /etc/init.d/denyhosts stop

Then remove your IP from /etc/hosts.deny

Then remove your IP from every file in:

/var/lib/denyhosts/

> sudo /etc/init.d/denyhosts start

---

