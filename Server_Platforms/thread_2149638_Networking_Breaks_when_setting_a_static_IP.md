---
title: "Networking Breaks when setting a static IP"
date: 2013-05-29
forum: Server Platforms
---

### Post by jpaytoncfd on 2013-05-29
using this guide [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/) I set my IP to static on my Ubuntu Server.

This worked for months. This weekend I tried to upgrade from scratch to 13.04. When I set the static IP I cant start networking through ```
init.d
``` or ```
service
```. even changing it back does not work. Once I try to change its totally broken. I stay connected until I restart and then I cant connect. I can set the interface up but still no connection.

---

### Post by rubylaser on 2013-05-29
The DNS nameserver portion of that tutorial needs to be updated for your newer version of Ubuntu.  Your static ip setup should go something like this now.

```

sudo -i
nano /etc/network/interfaces

```

```

auto eth0
iface eth0 inet static
     address 192.168.1.100
     netmask 255.255.255.0
     gateway 192.168.1.1
     dns-nameservers 8.8.8.8 8.8.4.4

```[COLOR=#333333][FONT=Verdana]

See if you can take the interface down and then back up with the if commands
```

ifdown eth0
ifup eth0

```[/FONT][/COLOR]

---

### Post by jpaytoncfd on 2013-05-29
I did it exactly like you said and it worked. Still not sure what I was doing wrong before besides the NS. anyway. thanks!

---

