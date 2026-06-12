---
title: "Ubuntu Server unable to connect to internet, but web server ok"
date: 2009-07-14
forum: Server Platforms
---

### Post by R.Bucky on 2009-07-14
So, I have a headless Ubuntu Server 8.04 that hosts my 7+ domains. I forward X11 through ssh to run FF3. I can access my domains using the browser, however I cannot access the internet. How can that be?

---

### Post by R.Bucky on 2009-07-15
This is what I currently use
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 10.1.10.XX
	netmask 255.255.255.0
	network 10.1.10.0
	broadcast 10.1.10.255
        gateway 10.1.10.1
```

Any ideas?

---

### Post by R.Bucky on 2009-07-15
[SOLVED] I misconfigured my /etc/resolv.conf. The nameserver was set to my internal lan versus the router! Doh!!

---

