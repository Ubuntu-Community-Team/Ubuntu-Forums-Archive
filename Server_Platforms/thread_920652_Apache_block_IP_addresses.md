---
title: "Apache block IP addresses"
date: 2008-09-15
forum: Server Platforms
---

### Post by boondocks on 2008-09-15
In "/etc/apache2/[COLOR="Blue"]apache2.conf[/COLOR]"
I would like to make a reference to "/etc/apache2/my_blocked_IPs.conf"

That way, I can update this "my_blocked_IPs.conf" with statements like:
deny from 192.168.5.5


And keep the "/etc/apache2/[COLOR="Blue"]apache2.conf[/COLOR]" as clean as possible.


Questions about the "/etc/apache2/[COLOR="Blue"]apache2.conf[/COLOR]":
[LIST=1]
[*]How should I make a reference to "/etc/apache2/my_blocked_IPs.conf" ?
[*]Where exactly in the apache2.conf file should the reference be located?
[/LIST]

---

