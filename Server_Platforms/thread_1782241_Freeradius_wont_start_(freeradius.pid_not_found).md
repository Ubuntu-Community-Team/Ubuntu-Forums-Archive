---
title: "Freeradius wont start (freeradius.pid not found)"
date: 2011-06-14
forum: Server Platforms
---

### Post by cavemanr on 2011-06-14
Guten Tag,

ich habe einen UbuntuServer 11.04 mit Bind9, DHCP, Apache2, PHP5, PostgreSQL8.4 im Betrieb und würde gerne noch eine Freeradius-Server aufsetzen. Das klappt auch alles soweit ganz gut bis auf die Tatsache, dass wenn ich den Server restarten möchte ich die Meldung:

Hello,

i run an 11.04 Server with Bind9, DHCP, Apache 2 PHP5, PostgreSQL8.4 and would like to install an FreeradiusServer. After I downloadet the packages with ```
apt-get install freeradius
``` I get this output

```
 * Stopping FreeRADIUS daemon freeradius
 * /var/run/freeradius/freeradius.pid not found...
   ...done.
 * Starting FreeRADIUS daemon freeradius
   ...fail!

```

Do u know this message after installing?

regards

cavemanr

---

### Post by kagisos on 2011-07-26
try purging freeradius(`apt-get purge freeradius`) and re-installing, i had some random problems aswell.. it might resolve it..

---

