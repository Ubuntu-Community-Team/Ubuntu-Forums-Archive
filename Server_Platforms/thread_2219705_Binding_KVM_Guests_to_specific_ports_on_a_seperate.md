---
title: "Binding KVM Guests to specific ports on a seperate interface"
date: 2014-04-25
forum: Server Platforms
---

### Post by bhima-pandava on 2014-04-25
I'm running a few KVM guests on 14.04 Server.  The wired interface (p2p1;192.168.2.11) is connected to the rest of my network via bridge (br0) and the guests all have IP addresses within 192.168.2.20-40.  These network configurations work fine.  The host machine can connect to the part of my network I wanted as well as the outside world... as can the guest machines.

I have now added a separate interface (ppp0) which connects to the internet via a 3G modem.  I wish to bind to specific ports of the guest machines to this external network.  For example: one guest machine (192.168.2.30) is running a webserver so I wish to redirect all incoming traffic on port 443 of ppp0 to it.  

However, I wish to ensure that *only* traffic on that port of the guest system connects to the ppp0 interface and all of other traffic flows through the wired interface.  For example I will only ssh in through the wired interface, not through pp0, and when I do a system update I wish for that traffic to flow through the wired interface.  Additionally I wish to ensure that ppp0 *only* connects these specified ports on the guest systems and *not* to the host system at all.

I suspect that this is best accomplished with IPTables but I am uncertain how to formulate the correct expression.  Reading the [KVM Networking Page]("https://help.ubuntu.com/community/KVM/Networking") I found a section which I think is very nearly part of what I need (Redirecting selected ports to virtual machines).  However, the example is to a static IP address in the same network segment as the guest, while I need to to redirect to an interface which is assigned an address by my ISP's dhcp server... and I'm sure I need to add expressions to drop all other traffic on ppp0.
```

iptables -t nat -A PREROUTING -d 192.168.0.10 -p tcp --dport 25 -j DNAT --to-destination 192.168.122.90:25
```

---

### Post by volkswagner on 2014-04-26
I am no iptables expert, but I think I can help get you started.
You can specify an network interface for the incoming bits.  For your port 443 example, simply
use ppp0 as the source iface adapter.

like:
```
-i pppo
```

I do recall an issue in the past with iptables and virtual interfaces.  My issue was iptables would not recognize eth1.1 but
I don't think you'll have the same issue.

Again I'm not an expert so I don't know if you'll use nat or forward or other ;)

---

