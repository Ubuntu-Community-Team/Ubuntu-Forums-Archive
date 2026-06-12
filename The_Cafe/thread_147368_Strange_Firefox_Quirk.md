---
title: "Strange Firefox Quirk"
date: 2006-03-20
forum: The Cafe
---

### Post by Kurt` on 2006-03-20
If you try to load any URL on port :6000, e.g. [http://somesite.com:6000](http://somesite.com:6000), Firefox throws up a message about it.

Anyone have any idea what the "security concern" is regarding port 6000?

---

### Post by dermotti on 2006-03-20
Thats the LovGate virus/worm port in windows. Im assuming they put it in there so you don't get forwarded to a site that has the virus and it infects you.

Its also this, for linux:

PORT 6000 - Information

Port Number:	6000
TCP / UDP:	TCP
Delivery:	Yes
Protocol / Name:	x11

TheThing trojan/virus
Port Description:	X-Window System. X11 ports to support remote x-windows sessions. Sessions are vulnerable to spoofing, session hijacking, capture of user screen data, keystroke monitoring, insertion of hostile keystrokes & commands, data diddling, and DOS. Review x-windows security techniques; do not run default x-windows server config's in production environment!.

---

