---
title: "dhcp server won't start at boot time"
date: 2009-08-30
forum: Server Platforms
---

### Post by irvken on 2009-08-30
I'm having trouble getting the dhcp-server to start on my ubuntu ltsp server on boot, I have to start it manually every time.

It appears there is a start up script in the right place for booting

/etc/rc5.d/S40dhcp3-server

?

---

### Post by drave on 2009-09-01
thats only good for runlevel 5. copy  the link to rc2.d and rc3.d as well

---

