---
title: "Server Can ONly Access Local Network with Static IP"
date: 2012-09-23
forum: Server Platforms
---

### Post by mattlach on 2012-09-23
Hey all,

I'm having a really odd issue.

I just upgraded my 11.11 server to 12.04, by performing a clean install.

I edited my /etc/network/interfaces file to the following:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

## The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.242
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

The iface, address, netmask, network, broadcast and gateway lines were copied and pasted from my old server, which worked perfectly.

However, now, whenever I set it static - as above - it can only reach the local network, noting outside on the internet.

When I set it back to DHCP, it uses the same IP, broadcast and netmask, but now it all of a sudden works just fine, and can reach outside networks.

```

eth0      Link encap:Ethernet  HWaddr 00:10:18:b2:00:ae
          inet addr:192.168.1.242  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:18ff:feb2:ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8195644 (8.1 MB)  TX bytes:1157572 (1.1 MB)
          Interrupt:19
```

Does anyone have any idea why this is happening?  It seems pretty strange to me.  Possibly some sort of bug?

For now, its OK, as the IP is the same anyway, but I don't trust DHCP, and I don't want the IP to change and my clients on the network all breaking their connections to it...

Appreciate any feedback.

Thanks,
Matt

---

### Post by steeldriver on 2012-09-23
Do you mean you can't access external IPs at all - or just that you can't access by name? maybe the difference is DHCP supplies DNS server info (which your static setup appears to be missing)?

If so I think you should be able to fix that (in the resolvconf way of doing things) by adding a dns-nameservers line to your iface stanza:

[http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html)

Possibly it worked on the old box because there was a DNS entry in /etc/resolv.conf?

---

### Post by mattlach on 2012-09-23
> **steeldriver said:**
> Do you mean you can't access external IPs at all - or just that you can't access by name? maybe the difference is DHCP supplies DNS server info (which your static setup appears to be missing)?

If so I think you should be able to fix that (in the resolvconf way of doing things) by adding a dns-nameservers line to your iface stanza:

[http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html)

Possibly it worked on the old box because there was a DNS entry in /etc/resolv.conf?

That sounds like it could be it.

Thank you very much!

--Matt

---

### Post by mattlach on 2012-09-23
Thank you.

That did turn out to be the case.

I added dns-nameservers and pointed it to my pfsense router, and now everything works. :)

I must have had the name servers in resolv.conf on the old server and not even noticed it.

---

### Post by steeldriver on 2012-09-23
yes the whole reolvconf / dnsmasq thing is taking a bit of getting used to - glad you fixed it anyhow

---

