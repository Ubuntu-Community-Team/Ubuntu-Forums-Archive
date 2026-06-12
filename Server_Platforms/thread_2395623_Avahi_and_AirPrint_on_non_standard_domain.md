---
title: "Avahi and AirPrint on non standard domain"
date: 2018-07-04
forum: Server Platforms
---

### Post by spbach1234 on 2018-07-04
My domain where my Ubuntu 18.04 server runs is .lan, not .local.  How do I get avahi to work with airprint with the nonstandard default domain setup?

---

### Post by TheFu on 2018-07-04
Can can configure avahi to use .lan, if you like. /etc/avahi/ is where I'd look.  After making any changes, which you'll need to make on all Unix machines on the subnet, restart avahi and wait 30-500 seconds.

Or just manage your network using DNS/static IPs.

---

### Post by spbach1234 on 2018-07-04
The server has a static ip of 10.0.0.3

If I change the Avahi config, it can't load my airprint service.

---

