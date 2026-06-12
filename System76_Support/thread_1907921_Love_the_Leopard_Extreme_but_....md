---
title: "Love the Leopard Extreme but ..."
date: 2012-01-12
forum: System76 Support
---

### Post by heartsbane on 2012-01-12
I have a brand new Leopard Extreme but ...

my ssh connections keep breaking: 

> Write failed: Broken pipe

It doesn't do it on my Lenovo T510 running ubuntu (same connection same cable) or my Macbook Pro (running ubuntu).

```
        *-network
             description: Ethernet interface
             product: 82567LF-2 Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 00
             serial: 70:71:bc:f1:bc:80
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=1.8-5 ip=10.0.0.99 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:59 memory:d2500000-d251ffff memory:d2523000-d2523fff ioport:4100(size=32)
```

I have even tried changing my /etc/ssh/ssh_config to add ServerAliveInterval to 10.

I really love the machine, but if my ssh connections keep breaking I don't know what I am going to do.

---

### Post by isantop on 2012-01-12
Are you connecting using the hostname of the system or the IP address? Also, does the machine have a static IP? I've seen these settings affect the reliability and stability of ssh connections in the past.

---

### Post by heartsbane on 2012-01-12
> **isantop said:**
> Are you connecting using the hostname of the system or the IP address? Also, does the machine have a static IP? I've seen these settings affect the reliability and stability of ssh connections in the past.

I use hostname and IP, and I am receiving a DHCP address

---

### Post by isantop on 2012-01-13
Are other network operations stable? If you try to download a large file, like an Ubuntu CD image, does this fail?

---

### Post by heartsbane on 2012-01-13
Yes there is 1-2 sec hiccup. I will try switching to a static IP

---

### Post by isantop on 2012-01-13
The fact that it seems to be dropping the connection for a bit indicates this is an issue with the card. Could you try running the computer from a Live disk to see if the issue happens there as well? Just boot from the Live Disk and attempt to recreate the issue. This will tell me if the problem is hardware or software.

---

### Post by heartsbane on 2012-01-13
I think I am narrowed it down to my DHCP lease time is to much is to soon and it drops during that. Because I have set it to static IP and it hasn't done it once yet (or atleast for the last 6 hours).

---

### Post by isantop on 2012-01-13
That's also a strong possibility. Go ahead and check what your lease time is set to in your router. We generally recommend at least 24 hours, though it may be useful to you to set it faster or slower than that.

---

