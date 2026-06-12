---
title: "Connecting to Windows VPN"
date: 2012-06-26
forum: Server Platforms
---

### Post by travisneids on 2012-06-26
I'm trying to create a VPN connection from my Ubuntu 10.04 LTS Server to a Windows VPN.  I'm able to connect with my Mac OS and ping the servers on the VPN network I need however this is not the case from the linux box.  

I am not running a desktop version of Ubuntu - all command line.

There are no issues connecting to the VPN but I can't ping anything on the server.

/etc/ppp/peers/myvpnfile
```

remotename foo
linkname foo
ipparam foo
pty "pptp the.vpn.address --nolaunchpppd"
name myuser
require-mppe
refuse-eap
noauth
file /etc/ppp/options.pptp

```

```
pppd call myvpnfile
```

ifconfig
```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:111.1.1.111  P-t-P:111.1.1.112  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:90 (90.0 B)  TX bytes:90 (90.0 B)
```
*Note not real ip but it looks like it should (same range as mac)

What am I missing?  What do you need for me to provided to get a better picture?

The plan is to connect to the drive using Samba.

---

### Post by travisneids on 2012-06-26
```
route add -net 10.0.0.0 netmask 255.0.0.0 dev ppp0
```

Solved it!

---

