---
title: "Can't bind to localhost after 10.04 upgrade (cherokee, php-cgi)"
date: 2010-05-17
forum: Server Platforms
---

### Post by PPvG on 2010-05-17
Hello everyone,

After upgrading Ubuntu, I'm having trouble with the cherokee (1.0.0) and php-cgi.

Cherokee itself runs fine. When I run **cherokee-admin**, I get this error:
[FONT="Courier New"][SIZE="3"](critical) bind.c:284 - Could not bind() port=9090 (UID=0, GID=0)[/SIZE][/FONT]

According to netstat port 9090 is absolutely free (both IPv4 and IPv6). When I run [FONT="Courier New"][SIZE="3"]cherokee-admin -b[/SIZE][/FONT] or [FONT="Courier New"][SIZE="3"]cherokee-admin -b0.0.0.0[/SIZE][/FONT] it will succesfully bind to :::9090 (IPv6) or 0.0.0.0:9090 (IPv4) respectively. I can then reach cherokee-admin via the public interface, but not via localhost (over an SSH tunnel). When I call [FONT="Courier New"][SIZE="3"]cherokee-admin[/SIZE][/FONT] with [FONT="Courier New"][SIZE="3"]-blocalhost[/SIZE][/FONT] or [FONT="Courier New"][SIZE="3"]-b127.0.0.1[/SIZE][/FONT] I get the same "Could not bind" error.

The same seems to happen with **php-cgi**. When I run  [FONT="Courier New"][SIZE="3"]/usr/bin/php-cgi -b 127.0.0.1:47990[/SIZE][/FONT], I get this error:
[FONT="Courier New"][SIZE="3"]Cannot bind/listen socket - [99] Cannot assign requested address.
Couldn't create FastCGI listen socket on port 127.0.0.1:47990[/SIZE][/FONT]

When I change 127.0.0.1 to localhost, I get this:
[FONT="Courier New"][SIZE="3"]Host 'localhost' has multiple addresses. You must choose one explicitly![/SIZE][/FONT]

I've tried [disabling IPv6]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html") and completely removing (with --purge) and reinstalling cherokee and all associated packages and libraries, but this didn't help either.

The problem started when I upgraded from Ubuntu 8.10 (via 9.04 and 9.10) to 10.04. It's a VPS with kernel 2.6.32.9 (domU, modified kernel for virtualization). Before the upgrade everything worked like a charm. I tried a 'fresh' install in a virtual machine on my local machine and everything works perfectly.

I'd rather not have to reinstall the complete server. Does anyone know what's going on?

---

### Post by PPvG on 2010-05-17
Anyone? Do I really have to completely reinstall the server for this tiny little problem?

---

### Post by Xipher on 2010-05-17
would you do a "ip addr show" and paste the output, thanks.

---

### Post by PPvG on 2010-05-18
Thank you for replying.

[FONT="Courier New"][SIZE="3"]ip addr show[/SIZE][/FONT]:
```
1: lo: <LOOPBACK> mtu 16436 qdisc noop state DOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether x:x:x:11:32:35 brd ff:ff:ff:ff:ff:ff
    inet x.x.97.103/24 brd x.x.97.255 scope global eth0
    inet6 x::x:x:fe11:3235/64 scope link
       valid_lft forever preferred_lft forever
3: dummy0: <BROADCAST,NOARP> mtu 1500 qdisc noop state DOWN
    link/ether x:x:x:16:69:70 brd ff:ff:ff:ff:ff:ff
4: tunl0: <NOARP> mtu 1480 qdisc noop state DOWN
    link/ipip 0.0.0.0 brd 0.0.0.0
5: gre0: <NOARP> mtu 1476 qdisc noop state DOWN
    link/gre 0.0.0.0 brd 0.0.0.0
```

---

### Post by PPvG on 2010-05-18
I finally found out what was wrong! In /etc/network/interfaces, I had this:
```
auto lo
iface lo inet loopback
pre-up iptables-restore < /etc/iptables.up.rules
        address 127.0.0.1
        netmask 255.0.0.0
```

The iptables-restore script causes an error, preventing the interface from going up. Commenting out the third line and running [FONT="Courier New"][SIZE="3"]sudo ifup lo[/SIZE][/FONT] fixed the problem! :D

---

### Post by dziamid on 2012-07-23
Use saved my from reinstalling my server! Thanks a TON!

---

