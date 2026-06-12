---
title: "cannot access from my public ip"
date: 2006-08-16
forum: Server Platforms
---

### Post by drs101 on 2006-08-16
Updated apache to the lastest version this morning and now I cannot access from my public ip, I can access from internal and localhost and port 80 is forwarded in my router config as it was before I upgraded.

Would the upgrade reset my apache config?

Any help would be great

Danny

---

### Post by mgor on 2006-08-16
it shouldn't have overwrite your config without asking you, but you could check /etc/apache2/ for *-dist or *-new files.

but afaik there's not default apache config that only allows traffic from certain networks. i think you should take a second look at your router config.

---

### Post by drs101 on 2006-08-16
thanks, recheck and it seems my ip has changed

Danny

---

### Post by Nano on 2006-08-17
For these kind of things it's recommended to have a dynamic ip service name, like ddclient/dyndns

---

