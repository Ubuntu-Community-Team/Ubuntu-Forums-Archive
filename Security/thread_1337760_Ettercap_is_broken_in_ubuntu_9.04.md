---
title: "Ettercap is broken in ubuntu 9.04"
date: 2009-11-25
forum: Security
---

### Post by sefs on 2009-11-25
Has anyone realized that ettercap is broken in ubuntu 9.04?

Running this command from a vm to another vm or to the host kills the internet connection of either.

```

sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward
ettercap -T -q -o -i wlan0 -M arp:remote /192.168.1.6/ /192.168.1.1/

```

---

