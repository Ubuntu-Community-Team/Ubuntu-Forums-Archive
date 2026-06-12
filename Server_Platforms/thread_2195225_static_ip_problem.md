---
title: "static ip problem"
date: 2013-12-23
forum: Server Platforms
---

### Post by feardotcom on 2013-12-23
I have Ubuntu 13.10 Sever installed and i set up a static ip and at first everything was fine. Then every morning i wake up to find my server has lost internet connection. If i use "sudo dhclient" and reboot, it goes back to working. I was doing some research and its because of my ISP, Comcast, DNS nameservers change ip addresses. I read that i need to set my dns server to my router which is the norm of 192.168.1.1. i remove all 3 entries and type the ip into resolv.conf. Either it doesn't accept it, or it changes it back. When i reopen resolv.conf it shows nothing. What am i doing wrong?

---

### Post by nerdtron on 2013-12-23
You should not edit the resolv.conf by hand. Do you want to configure static IP on your server? Please post your /etc/network/interfaces file.

---

### Post by feardotcom on 2013-12-23
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.60
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by SeijiSensei on 2013-12-24
Add this line after the "gateway" directive for eth0:

```
dns-nameservers 10.10.10.10 10.10.10.11 10.10.10.12
```

using the IP addresses of the server(s) you prefer.  Note the ending "s" in "nameservers"; it's easy to leave off by mistake.

---

