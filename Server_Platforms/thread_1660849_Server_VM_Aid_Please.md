---
title: "Server VM Aid Please"
date: 2011-01-05
forum: Server Platforms
---

### Post by MusicJunkie on 2011-01-05
Does anyone know how to make a Ubuntu 10.04 server VM look for an IPv4 address if it doesn't seem to by default?

---

### Post by aceofspades686 on 2011-01-05
Which VM software are you using? If your DHCP server isn't handing out an IP by default, you may have the network interfaces improperly configured.

---

### Post by kevinthecomputerguy on 2011-01-06
Goto Directory /etc/modprobe.d
 
edit alaises file, change #10 from "ipv6" to "off"
 
and or
 
edit blacklists file, and add "ipv6"
 
then reboot

---

### Post by MusicJunkie on 2011-01-06
I'm not sure which VMs player we are using. We know the dhcp is handing out ip addresses because the windows xp VMs are getting an address.

---

