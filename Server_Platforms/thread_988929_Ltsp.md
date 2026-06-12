---
title: "Ltsp"
date: 2008-11-21
forum: Server Platforms
---

### Post by mitchroberts on 2008-11-21
problem i am trying to log into my home linux terminal server 
from my laptop at work over the internet but it will not connect
anyone have any ideas how to do this? I am using ubuntu 8.04 
terminal server and ubuntu 8.04 desktop.

---

### Post by Vegan on 2008-11-21
is the machine behind a wireless box? if it is you need to open the ports manually. This only works if the machine uses a static IP above or below the wireless box's local IP range.

Eg DHPC is 100-150 then you can use 2-99 and leave room to extend the DHCP if needed.

:guitar:

---

### Post by mitchroberts on 2008-11-22
> **Vegan said:**
> is the machine behind a wireless box? if it is you need to open the ports manually. This only works if the machine uses a static IP above or below the wireless box's local IP range.

Eg DHPC is 100-150 then you can use 2-99 and leave room to extend the DHCP if needed.

:guitar:

at work it is but at home i have a hard line

---

