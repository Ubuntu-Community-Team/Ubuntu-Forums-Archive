---
title: "How can I get my domain to appear on outgoing connection?"
date: 2007-01-15
forum: Server Platforms
---

### Post by CzarAlex on 2007-01-15
I would like my domain which points to an ubuntu server hosted at my house, (we`ll call it site.com) to be displayed as my connection source when an outgoing connection is made, instead of (again, we`ll say) c-68-82-215-239.hsd1.pa.comcast.net.

Examples of where this would be displayed include but are not limited to, IRC connections, when SSH`ing to someone's box, when I log in to a MOO/MUD. 

The DNS for my site is done through zoneedit but I dont think that would govern anything dealing with an outbound connection from my server. Suggestions? :-k

---

### Post by MrHorus on 2007-01-15
> **CzarAlex said:**
> I would like my domain which points to an ubuntu server hosted at my house, (we`ll call it site.com) to be displayed as my connection source when an outgoing connection is made, instead of (again, we`ll say) c-68-82-215-239.hsd1.pa.comcast.net.


This can't be done since this is reverse delegation, not forward.

Reverse delegation is generally controlled by who owns the IP Address (Comcast in this instance) and this is something that is rarely delegated to end users.

You can ask but I wouldn't get your hopes up.

---

### Post by CzarAlex on 2007-01-15
Ah. Thanks for the update.

---

