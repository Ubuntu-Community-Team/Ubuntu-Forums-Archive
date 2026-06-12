---
title: "Sysctl.conf settings do not get applied at boot !"
date: 2023-03-08
forum: Server Platforms
---

### Post by Anquietas on 2023-03-08
Hello,

I have another wierd problem, this time regarding IPv6 on Ubuntu Server. (22.04.1 LTS)

I have some settings in sysctl.conf regarding my particular IPv6 settings, as this Server acts as a Router (being a Linux Router) and my ISP provides me with PPPoE with IPv4 and RA for IPv6.

The lines in **sysctl.conf**:
```

#IPv6 Tweaks:
        # Disable (Allow only LAN and PPP0 with IPv6 addresses):
net.ipv6.conf.lan.disable_ipv6=0
net.ipv6.conf.hw.disable_ipv6=1
net.ipv6.conf.wan.disable_ipv6=1
net.ipv6.conf.ppp0.disable_ipv6=0
net.ipv6.conf.tun0.disable_ipv6=1

        # Disable Autoconf on LAN (use fe80::1 instead):
net.ipv6.conf.lan.autoconf=0

        # Accept RA from PPP:
net.ipv6.conf.ppp0.autoconf=1
net.ipv6.conf.ppp0.accept_ra=2

```

However, I don't have IPv6 connectivity after Boot.
In the past, I HAD !
So something must have happened via an Update, for example ?...

Examining the Logs reveal the following:
```

Mar  8 00:04:20 infosky lynis[2457]: - Checking IPv6 configuration [ ENABLED ]
Mar  8 00:04:20 infosky lynis[2457]: IPv6 only [ NO ]
Mar  8 00:04:40 infosky lynis[2457]: - net.ipv6.conf.all.accept_redirects (exp: 0) [ DIFFERENT ]
Mar  8 00:04:40 infosky lynis[2457]: - net.ipv6.conf.all.accept_source_route (exp: 0) [ OK ]
Mar  8 00:04:40 infosky lynis[2457]: - net.ipv6.conf.default.accept_redirects (exp: 0) [ DIFFERENT ]
Mar  8 00:04:40 infosky lynis[2457]: - net.ipv6.conf.default.accept_source_route (exp: 0) [ OK ]
Mar  8 00:13:41 infosky systemd-sysctl[457]: Couldn't write '0' to 'net/ipv6/conf/ppp0/disable_ipv6', ignoring: No such file or directory
Mar  8 00:13:41 infosky systemd-sysctl[457]: Couldn't write '1' to 'net/ipv6/conf/tun0/disable_ipv6', ignoring: No such file or directory
Mar  8 00:13:41 infosky systemd-sysctl[457]: Couldn't write '1' to 'net/ipv6/conf/ppp0/autoconf', ignoring: No such file or directory
Mar  8 00:13:41 infosky systemd-sysctl[457]: Couldn't write '2' to 'net/ipv6/conf/ppp0/accept_ra', ignoring: No such file or directory
Mar  8 00:13:41 infosky kernel: [    0.804740] Segment Routing with IPv6
Mar  8 00:13:41 infosky kernel: [    0.804773] In-situ OAM (IOAM) with IPv6
Mar  8 00:13:41 infosky kernel: [  100.699249] IPv6: ADDRCONF(NETDEV_CHANGE): lan: link becomes ready
Mar  8 00:13:48 infosky dhcpcd[822]: ppp0: soliciting an IPv6 router
Mar  8 00:13:48 infosky systemd-networkd[780]: lan: Gained IPv6LL
Mar  8 00:13:49 infosky systemd[1]: Starting Router advertisement daemon for IPv6...
Mar  8 00:13:49 infosky systemd[1]: Started Router advertisement daemon for IPv6.
Mar  8 00:13:49 infosky dhcpcd[822]: ppp0: soliciting an IPv6 router
Mar  8 00:13:50 infosky systemd-networkd[780]: ppp0: Gained IPv6LL
Mar  8 00:13:50 infosky systemd[1]: Started ISC DHCP IPv6 server.
Mar  8 00:13:52 infosky sh[1103]: No subnet6 declaration for hw (no IPv6 addresses).
Mar  8 00:13:52 infosky sh[1103]: No subnet6 declaration for wan (no IPv6 addresses).
Mar  8 00:13:52 infosky dhcpd[1103]: No subnet6 declaration for hw (no IPv6 addresses).
Mar  8 00:13:52 infosky dhcpd[1103]: No subnet6 declaration for wan (no IPv6 addresses).
Mar  8 00:13:55 infosky systemd-networkd[780]: tun0: Gained IPv6LL
Mar  8 00:13:55 infosky ovpn-valhalla[1115]: Could not determine IPv4/IPv6 protocol. Using AF_INET
Mar  8 00:14:06 infosky dhcpcd[822]: ppp0: no IPv6 Routers available
Mar  8 00:14:06 infosky dhcpcd[822]: ppp0: no IPv6 Routers available

```

So, what is **Couldn't write '2' to 'net/ipv6/conf/ppp0/accept_ra', ignoring: No such file or directory** ?
This is wierd !

At a close examination:
```

infosky [~] # cat /proc/sys/net/ipv6/conf/ppp0/accept_ra
0
infosky [~] # 

```

If I **echo 2 > /proc/sys/net/ipv6/conf/ppp0/accept_ra**, everything starts working OK, because the RAs are accepted again.

However, some of my options in Sysctl.conf are already set. Maybe they are defaults ? or maybe they got set in the first place ?
I am clearly having trouble with **accept_ra**, which, in the past, used to work properly !

I am assuming it has something to do with that message that **it could not write those values to the files**.
But why ? Is the script initialized to early, when those virtual files are still not fully loaded ? Or what is happening ?

Thank you !

---

### Post by TheFu on 2023-03-08
See if systemd honors any of those settings.  A few years ago, that team decided the only way to disable ipv6 was using grub settings.  Do some research in the systemd documentation to learn more.

They broke a few other things that had been working 20+ yrs, so whenever you look up answers, you'll need to ensure the answer isn't too old and isn't being overridden by some new software.  Unfortunately.

---

### Post by #&amp;thj^% on 2023-03-08
in /etc/sysctl.conf

```
net.ipv6.conf.default.autoconf = 1
net.ipv6.conf.default.forwarding = 2
net.ipv6.conf.default.accept_ra = 2

net.ipv6.conf.all.autoconf = 1
net.ipv6.conf.all.forwarding = 2
net.ipv6.conf.all.accept_ra = 2
```
might need an executable script to bring that interface up.
Just an Example only
an executable file in /etc/ppp/ipv6-up.d that does:
```
sysctl -w net.ipv6.conf.ppp1.accept_ra=2
```

---

### Post by Anquietas on 2023-03-10
Thank you, I will try this ! :)

---

### Post by MAFoElffen on 2023-03-10
I'm wondering if it is a timing issue, where device ppp0 is not there yet in /proc/sys/net/ipv6/conf/... But comes up later? You could always reread and reset the values from /etc/sysctl.conf via
```

sudo sysctl -p

```

---

