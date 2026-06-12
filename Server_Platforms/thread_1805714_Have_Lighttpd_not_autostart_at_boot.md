---
title: "Have Lighttpd not autostart at boot"
date: 2011-07-16
forum: Server Platforms
---

### Post by leegold on 2011-07-16
Hi,

How do I stop Lighttpd server from auto starting when I boot? I'm using it on my laptop for testing and I'd like to turn it on when I need it but not have it autostart.

Using 11.04

Thanks

---

### Post by brumm on 2011-07-16
Hi,

provided the service is called lighttpd:

update-rc.d -f lighttpd remove
update-rc.d lighttpd stop 80 0 1 2 3 4 5 6 .
echo manual > /etc/init/lighttpd.override


Bye,
brumm

---

