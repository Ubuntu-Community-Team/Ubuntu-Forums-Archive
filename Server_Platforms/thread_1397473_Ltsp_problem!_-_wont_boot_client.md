---
title: "Ltsp problem! - wont boot client"
date: 2010-02-03
forum: Server Platforms
---

### Post by police512 on 2010-02-03
HEY,

i have a ubuntu desktop edition witch i turned into server, and i was trying the ubuntu ltsp and i installed it and edited the config file but cannot get any computers to boot? :S so if anyone could help me then plz i have pics which il upload

---

### Post by police512 on 2010-02-06
Does no-one know how to fix this??

---

### Post by nobrac on 2010-02-07
In your dhcpd.conf you've declared a subnet for 192.168.0.0/24 but you're serving IP addresses from 192.168.1.0/24. I imagine the LTSP client is somewhat confused...

---

