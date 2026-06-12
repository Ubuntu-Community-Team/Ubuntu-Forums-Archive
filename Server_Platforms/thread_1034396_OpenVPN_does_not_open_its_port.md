---
title: "OpenVPN does not open its port"
date: 2009-01-08
forum: Server Platforms
---

### Post by jackhab on 2009-01-08
Hi
I setup OpenVPN on Ubuntu 8.1 server and when I launch the server I got the following output which seems OK to me:
```
Thu Jan  8 16:27:16 2009 OpenVPN 2.1_rc11 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 15 2008
Thu Jan  8 16:27:16 2009 Diffie-Hellman initialized with 1024 bit key
Thu Jan  8 16:27:16 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Thu Jan  8 16:27:16 2009 TLS-Auth MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Thu Jan  8 16:27:16 2009 ROUTE default_gateway=10.0.0.138
Thu Jan  8 16:27:16 2009 TUN/TAP device tun0 opened
Thu Jan  8 16:27:16 2009 TUN/TAP TX queue length set to 100
Thu Jan  8 16:27:16 2009 /sbin/ifconfig tun0 10.8.0.1 pointopoint 10.8.0.2 mtu 1500
Thu Jan  8 16:27:16 2009 /sbin/route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.0.2
Thu Jan  8 16:27:16 2009 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Thu Jan  8 16:27:16 2009 Socket Buffers: R=[124928->131072] S=[124928->131072]
Thu Jan  8 16:27:16 2009 UDPv4 link local (bound): [undef]:1194
Thu Jan  8 16:27:16 2009 UDPv4 link remote: [undef]
Thu Jan  8 16:27:16 2009 MULTI: multi_init called, r=256 v=256
Thu Jan  8 16:27:16 2009 IFCONFIG POOL: base=10.8.0.4 size=62
Thu Jan  8 16:27:16 2009 IFCONFIG POOL LIST
Thu Jan  8 16:27:16 2009 Initialization Sequence Completed

```

However when I run nmap:
```
Starting Nmap 4.62 ( http://nmap.org ) at 2009-01-08 16:27 IST
Interesting ports on localhost (127.0.0.1):
Not shown: 1702 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
53/tcp   open  domain
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
953/tcp  open  rndc
3306/tcp open  mysql
3389/tcp open  ms-term-serv
5432/tcp open  postgresql
5900/tcp open  vnc
5901/tcp open  vnc-1
6001/tcp open  X11:1

Nmap done: 1 IP address (1 host up) scanned in 0.055 seconds
```

Why the OpenVPN port 1194 is not open? What have I missed?

Thanks.

---

### Post by albinootje on 2009-01-08
> **jackhab said:**
> 
Nmap done: 1 IP address (1 host up) scanned in 0.055 seconds[/CODE]

Why the OpenVPN port 1194 is not open? What have I missed?

OpenVPN uses udp and not tcp by default.

---

### Post by jackhab on 2009-01-08
Sorry
```
Starting Nmap 4.62 ( http://nmap.org ) at 2009-01-08 16:57 IST
Interesting ports on localhost (127.0.0.1):
Not shown: 1481 closed ports
PORT     STATE         SERVICE
53/udp   open|filtered domain
68/udp   open|filtered dhcpc
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
177/udp  open|filtered xdmcp
631/udp  open|filtered unknown
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.638 seconds

```

---

### Post by cdenley on 2009-01-08
```

sudo netstat -tulnp

```

---

