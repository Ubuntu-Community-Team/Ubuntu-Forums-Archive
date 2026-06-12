---
title: "No internet access from server, but hosting (https, http, ftp, ssh, etc) works fine.."
date: 2011-07-07
forum: Server Platforms
---

### Post by weryl on 2011-07-07
Hi all,

I've recently upgrade my server to ubuntu 11.04 and, though the server daemons work fine (apache2, ssh, ftp, etc.), I can't seem to go on the internet anymore (lynx, apt-get, ping).

So to make it clear I can access the server just fine, but the server can't access anything else.

Has anyone had that problem?

Thank you,

Mike

---

### Post by rubylaser on 2011-07-07
Sounds like your gateway may be messed up on your server if all other network traffic on the LAN is still working.  What's the output of this...
```
cat /etc/network/interfaces
```
and
```
route -n
```
and
```
ifconfig
```

---

### Post by weryl on 2011-07-07
Thanks alot for your time! Here's what these commands returned:

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

#iface eth0 inet static
#       address 192.168.1.2
#       gateway 192.168.1.1
#       netmask 255.255.255.0
#       network 192.168.1.0
#       broadcast 192.168.1.255
```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

```

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:29:4c:e1:41
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe4c:e141/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4969217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6041469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:142007 txqueuelen:1000
          RX bytes:2591119575 (2.5 GB)  TX bytes:2053614546 (2.0 GB)
          Interrupt:11 Base address:0xb800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4653044 (4.6 MB)  TX bytes:4653044 (4.6 MB)
```

Anything wrong there?

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
Have you allowed the HTTP(80) & HTTPS(443) protocols IN through your firewall?

---

### Post by spynappels on 2011-07-08
Can you ping using IP addresses? For example, can you ping 8.8.8.8?
If you can, you have a problem with your dns settings and you can fix it by editing the resolv.conf file

```
sudo nano /etc/resolv.conf
```

Add the following lines

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

These are Google's nameservers. You can also enter the DNS servers supplied by your ISP instead.

---

### Post by spynappels on 2011-07-08
> **headvampyre@hotmail.co.uk said:**
> Have you allowed the HTTP(80) & HTTPS(443) protocols IN through your firewall?

Not sure why that is relevant? If he is trying to access external content, he is not using those ports inbound anyway.

---

### Post by david.garceau on 2011-07-08
I second this, seems like a dns issue

> **spynappels said:**
> Can you ping using IP addresses? For example, can you ping 8.8.8.8?
If you can, you have a problem with your dns settings and you can fix it by editing the resolv.conf file

```
sudo nano /etc/resolv.conf
```

Add the following lines

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

These are Google's nameservers. You can also enter the DNS servers supplied by your ISP instead.

---

### Post by weryl on 2011-07-09
> **spynappels said:**
> Can you ping using IP addresses? For example, can you ping 8.8.8.8?
If you can, you have a problem with your dns settings and you can fix it by editing the resolv.conf file

```
sudo nano /etc/resolv.conf
```

Add the following lines

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

These are Google's nameservers. You can also enter the DNS servers supplied by your ISP instead.

Thanks alot! That did it, and now ping/lynx/apt-get work perfectly :)

Edit: Btw do you have any idea why this happened? Everything was fine before the upgrade to natty.

---

### Post by Wim Sturkenboom on 2011-07-09
Because you're lucky if upgrades work flawlesly ;)

Any reason why you're not running LTS versikons on a server ?

---

### Post by weryl on 2011-07-10
> **Wim Sturkenboom said:**
> Because you're lucky if upgrades work flawlesly ;)

Any reason why you're not running LTS versikons on a server ?
No good reason really, I'll try to be more careful in the future :/

---

### Post by spynappels on 2011-07-11
Glad you got it sorted, sometimes the resolv.conf may be overwritten with a new/blank one during an upgrade, I've also seen it happen when switching between DHCP and Static a few times.

---

