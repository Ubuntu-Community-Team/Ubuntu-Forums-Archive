---
title: "Server Connection Problems"
date: 2009-11-09
forum: Server Platforms
---

### Post by kahuna0789 on 2009-11-09
Hello all,
I have done a great deal of searching on this issue and I cannot find a solution to my problem that works.

my setup: my server (ubuntu 9.10 server)  is directly connected to my linksys router via eth0 (and this is the exact setup this server has been in for the last year... until the hard drive crashed a week ago)

On install when i was asked for network information I chose to manual in order to get a specific address.

The configuration was something like this
```
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
nameserver x.x.x.148 x.x.x.147 127.0.0.1 192.168.1.1
```now that it is finished installing I cannot access the internet or even ping my local network addresses.

I have tried verifying /etc/network/interfaces and /etc/resolv.conf which provides the same information

I have also tried to setup a default route using
```
route add default gw 192.168.1.1
```this does not return an error... but it still does not allow me to access anything on the network

I have also tried setting up eth0 (and others) as dhcp and when I restart /etc/init.d/networking it fails to receive a DHCP response.

Does anyone see anything I have missed?

---

### Post by BQAggie2006 on 2009-11-09
Can you post the output of:

```
cat /etc/network/interfaces
```

---

### Post by kahuna0789 on 2009-11-09
Here is the file without all of the commented lines

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

---

### Post by Iowan on 2009-11-09
**ifconfig -a** and **route -n** confirm that your manual entries got applied?
The cable is OK?

---

### Post by kahuna0789 on 2009-11-10
My cable tester says that the cable is fine

ifconfig -a returns the expected results and route -n returns
```
Kernel IP routing table
Destination    Gateway       genmask        Flags    Metric    Ref    Use    Iface
192.168.1.0    0.0.0.0       255.255.255.0  U        0         0      0      eth0
0.0.0.0        192.168.1.1   0.0.0.0        UG       100       0      0      eth0
```Note: I'm not sure if it makes a difference but there was a typo in my first post, the server version should have been 9.10 instead of 8.10

---

### Post by doas777 on 2009-11-10
ok, can you do an nslookup? your problem may be dns resolution. 
I would start by dropping the network and broadcast lines from your interfaces file unless you need them (your values are generic so you don't).

I'm worried about the loopback in your nameserver list. what is in \etc\resolv.conf?
also can you post the ifconfig anyway?

---

### Post by kahuna0789 on 2009-11-10
nslookup just hangs, i have removed 192.168.1.1 and the loopback from /etc/resolv.conf so now it just has the two dns addresses i found when i did ipconfig on this computer

i also commented out the network and broadcast lines and restarted networking. No help :(

the output of ifconfig eth0
```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```mac address omitted but the rest is an exact copy

---

### Post by Iowan on 2009-11-10
Firewall running?

---

### Post by kahuna0789 on 2009-11-10
I disabled UFW as soon as i started having problems, i probably should have mentioned that earlier.
I'm starting to wonder if maybe I got a bad burn of the ISO because i had to reinstall as soon as i installed the OS the other day because it failed to boot. Luclky reinstalling fixed the boot time issue but this one persists.

---

