---
title: "iptables Setup"
date: 2011-02-16
forum: Server Platforms
---

### Post by stevetheman on 2011-02-16
I'm setting up a VPS I just got a couple of days ago and just want to make sure that I'm doing it right for the iptables.

In my /etc/network/interfaces I have the loopback interface as lo and that's where my pre-up line for iptables is, but that's not the interface with 127.0.0.1 as it's ip address. That's with an interface venet0 (which I assume is there becase I'm on a VPS under OpenVZ).

The file looks like this:

```

auto lo
iface lo inet loopback
pre-up iptables-restore < /etc/iptables.up.rules

auto venet0
iface venet0 inet static[INDENT]address 127.0.0.1
netmask 255.255.255.255
broadcast 0.0.0.0
up route add -net 192.0.2.1 netmask 255.255.255.255 dev venet0
up route add default gw 192.0.2.1
[/INDENT]

```

Should the line for iptables be with venet0 or lo?

---

### Post by elico on 2011-02-17
it doesn't matter what you need is for the os to load the iptables rules.
as long as the command runs at computer start-up it's fine.
if you do want to make sure the firewall rules are up without any connection to the network up thing you can create a new script for it on the /etc/init.d/ 
directory

---

