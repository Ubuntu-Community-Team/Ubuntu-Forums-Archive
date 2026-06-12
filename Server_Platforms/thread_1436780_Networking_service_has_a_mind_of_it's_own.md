---
title: "Networking service has a mind of it's own"
date: 2010-03-23
forum: Server Platforms
---

### Post by AdrianNitescu on 2010-03-23
Hello there.

I have some trouble with my networking.
I have in /etc/network/interfaces eth0 with ip 86.*.252 and eth0:2 with ip 86.*.38.
If I restart networking, this is the ifconfig output:

```
root@phpqa:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:05:43:7f:55
          inet addr:86.<>.252  Bcast:86.<>.255  Mask:255.255.255.192
          inet6 addr: fe80::230:5ff:fe43:7f55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:54446759 (54.4 MB)  TX bytes:26919527 (26.9 MB)

eth0:1    Link encap:Ethernet  HWaddr 00:30:05:43:7f:55
          inet addr:62.<>.57  Bcast:62.<>.63  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:2    Link encap:Ethernet  HWaddr 00:30:05:43:7f:55
          inet addr:86.<>.38  Bcast:86.<>.63  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17539 (17.5 KB)  TX bytes:17539 (17.5 KB)
```

If I restart the box. On eth0:1 appears another ip 86.*.253 which is on an router. And the make ip conflict.
Something is not right here. I just want networking to respect /etc/network/interfaces

What's happening?

Thanks,
Adrian

---

### Post by Exca on 2010-03-23
Hi AdrianNitescu,

Does eth0:1 seems to take an IP from a DHCP server ?
Can you show us your /etc/network/interfaces ?

---

### Post by KB1JWQ on 2010-03-23
Let me guess, you have the NetworkManager service running?

I despise that thing. :-/

---

### Post by AdrianNitescu on 2010-03-25
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 86.<>.252
        netmask 255.255.255.192
        network 86.<>.192
        broadcast 86.<>.255
        gateway 86.<>.193
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 82.76.253.115 82.76.253.125
        dns-search info
auto eth0:0
iface eth0:0 inet static
        address 86.<>.38
        netmask 255.<>.192
        gateway 86.<>.1
```

It's very weird. The *.253 ip was used some time ago and the *.38 on the router. I switched them because *.253 it's on every living spam database.

Thanks

---

### Post by Exca on 2010-03-25
Where are configured your eth0:1 and eth0:2 interfaces ? :???:

---

### Post by AdrianNitescu on 2010-03-25
0:1 I configured it via command line. I needed an extra IP.
0:2 should be 0:0 but is said it cannot be allocated or something like that.

---

### Post by Exca on 2010-03-25
> **AdrianNitescu said:**
> 
If I restart the box. On eth0:1 appears another ip 86.*.253 which is on an router. And the make ip conflict.
Something is not right here. I just want networking to respect /etc/network/interfaces


So, you don't set manually your eth0:1 in /etc/network/interfaces. Did it takes an IP from a DHCP or you've set it manually ?

---

### Post by AdrianNitescu on 2010-03-25
@Exca:

The ifconfig looks like that right now. If I reboot the computer. On eth0:1 I have *.253 and on eth0:2 *.38. The server conflicts with the router which currently holds the *.252 ip and I have to **ifconfig eth0:1 down** to have network.
I didn't configure anything beside the interfaces file. Theoretically after reboot I should have on eth0 *.252 and on eth0:0 *.38.
Everything is static. No DHCP.

---

