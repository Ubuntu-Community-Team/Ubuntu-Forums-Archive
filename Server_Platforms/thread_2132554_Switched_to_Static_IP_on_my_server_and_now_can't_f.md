---
title: "Switched to Static IP on my server and now can't find nameserver"
date: 2013-04-05
forum: Server Platforms
---

### Post by matthewboh on 2013-04-05
I have several machines in my network and two servers. The second server, I just loaded up with Ubuntu 12.10 server edition. I wanted to change it to a static IP address. I updated the /etc/network/interfaces file to read

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        wpa-ssid mywpaname
        wpa-psk  mysupersecretpassword
```

Everything seems to work EXCEPT for dns names. For example, I can get the IP address for google.com and ping it. However, I cannot run ping google.com - just get an unknown host error.

I've tried adding nameserver 8.8.8.8 to the interfaces file - but that didn't work. I've looked at the resolv.conf file, but it tells me not to modify it.

What should I be doing here?

Thanks

---

### Post by darkod on 2013-04-05
I can't find anything exact on google right now, but try 'nameservers'.

I think in /etc/resolv.conf (which now you shouldn't edit manually) it was used 'nameserver' and different servers are in different lines, but in /etc/network/interfaces with an S at the end, and the different servers are separated by a space. Try:
nameservers 8.8.8.8

You can also drop the network and broadcast options, they are calculated automatically. But it doesn't matter if they stay there.

---

### Post by steeldriver on 2013-04-05
it's *dns-nameservers* I think e.g.

```
auto wlan0
iface wlan0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        wpa-ssid mywpaname
        wpa-psk  mysupersecretpassword
        **dns-nameservers 8.8.8.8 8.8.4.4**

```

[http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html)

---

### Post by darkod on 2013-04-05
Spot on. :)

---

### Post by matthewboh on 2013-04-05
That worked! Thanks!

---

