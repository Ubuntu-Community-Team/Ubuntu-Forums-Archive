---
title: "Static route disappears"
date: 2008-05-13
forum: Server Platforms
---

### Post by doc_holiday on 2008-05-13
When I add the following route on the firewall after a few days is disappears.

route add -net 192.168.0.0/16 dev tun0

---

### Post by bluefrog on 2008-05-13
when you reboot surely?

---

### Post by doc_holiday on 2008-05-13
> **bluefrog said:**
> when you reboot surely?

No at random times. 4 times in the last 2 weeks and the server has not been rebooted in 29 days.

---

### Post by juan@forum on 2008-05-14
you need to adjust the /etc/network/interfaces file a little bit


example:

auto eth0
iface eth0 inet static
   address 192.168.100.23
   network 192.168.100.0
   gateway 192.168.100.1
   up "/sbin/route add -net ... "
   down "/sbin/route del -net ... "

---

### Post by doc_holiday on 2008-05-14
It is not an interface on the server. It should only know that he has to route it over his vpn tunnel.

---

### Post by netztier on 2008-05-14
> **doc_holiday said:**
> It is not an interface on the server. It should only know that he has to route it over his vpn tunnel.

In that case you should make sure that the route's installation or removal depends on the VPN tunnel's presence or "up" state, just as the other poster suggested to make it depend on an interface's "up" state.

What kind of software do you use to build that VPN tunnel? Check it's documentation to see if it allows for adding routes after the tunnel has come up.

regards

Marc

---

### Post by doc_holiday on 2008-05-14
I use openvpn, and the server acts as the openvpn gateway. So there are always tunnels present.

---

