---
title: "DNS (bind9) No Longer Resolving"
date: 2012-10-08
forum: Server Platforms
---

### Post by jlacroix on 2012-10-08
For some reason, DNS stopped working in my home network. I'm not sure when this started, I don't test it every day. Basically, I'm using bind in my home network for local DNS resolving. When I ping a host from my DNS server (Hermes) it works fine and shows the proper IP. But if I ping from any other PC, it does not work. I don't understand why this isn't working. I don't remember changing anything, other than setting up a few DHCP reservations, which I wouldn't think would effect DNS.

When I ping a host from any other PC, I get:
```
64 bytes from hit-nxdomain.opendns.com (67.215.65.132): icmp_req=2 ttl=56 time=29.4 ms
```
That looks like it's the ISP domain that is responding and not my local PC.

Here is my /etc/bind/net.localnet:
```

; dns zone for for localnet
;

$TTL 1D

; any time you make a change to the domain, bump the
; "serial" setting below. the format is easy:
; YYYYMMDDI, with the I being an iterator in case you
; make more than one change during any one day

@ IN SOA localnet. hostmaster.localnet. (

201210081 ; serial

8H ; refresh
4H ; retry
4W ; expire
1D ) ; minimum
IN A 172.16.254.5
;
@ IN NS hermes.localnet.
athena          IN      A       172.16.254.13
ceres           IN      A       172.16.254.11
eris            IN      A       172.16.254.14
hermes          IN      A       172.16.254.5
nyx             IN      A       172.16.254.28
pluto           IN      A       172.16.254.10
trinity         IN      A       172.16.254.12
zeus            IN      A       172.16.254.4

; bla           IN      CNAME   hermes ; Example of a CNAME record, if nec$
; www           IN      A       172.16.254.5 ; Example of a www record

```



And my /etc/bind/revp.172.16.254:
```

; reverse pointers for 172.16.254.0 subnet
;
$TTL 1D
@ IN SOA hermes.localnet. hostmaster.localnet. (
201210081 ; serial
28800 ; refresh (8 hours)
14400 ; retry (4 hours)
2419200 ; expire (4 weeks)
86400 ; minimum (1 day)
)
;
@ NS hermes.localnet.
4       PTR     zeus.localnet.
5       PTR     hermes.localnet.
10      PTR     pluto.localnet.
11      PTR     ceres.localnet.
12      PTR     trinity.localnet.
13      PTR     athena.localnet.
14      PTR     eris.localnet.
28      PTR     nyx.localnet.

```

I appreciate any help, I'mm still a beginner with bind so please go easy on me.

---

### Post by Doug S on 2012-10-08
I do not think your problem is with bind.
I think your problem is that, somehow, your other computers have forgotten that 172.16.254.5 is their primary DNS server.

---

### Post by newbie-user on 2012-10-08
Make sure you're specifying your local DNS as your network's primary DNS in your DHCP settings.

---

### Post by jlacroix on 2012-10-08
> **newbie-user said:**
> Make sure you're specifying your local DNS as your network's primary DNS in your DHCP settings.
You guys might be on to something. I thought it was all my PCs that can't ping my hosts through DNS, but it appears to only by my file server (a seperate server than the DNS server).

However, I'm pretty sure I have the addressing set up properly. Here's /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 172.16.254.10
        netmask 255.255.255.0
        network 172.16.254.0
        broadcast 172.16.254.255
        gateway 172.16.254.1

dns-search localnet
dns-nameservers 172.16.254.5, 172.16.254.1

```

Edit: I also shoudl point out that I'm getting horrible ping times. About a half second each ping!

---

### Post by Doug S on 2012-10-09
I agree everything looks O.K. Do you actually have another DNS at 172.16.254.1? Perhaps run tcpdump looking for traffic for port 53 and observe what is happening at the packet level.```
sudo tcpdump -n -nn -tttt -i eth0 port 53
```

---

### Post by jlacroix on 2012-10-09
> **Doug S said:**
> I agree everything looks O.K. Do you actually have another DNS at 172.16.254.1? Perhaps run tcpdump looking for traffic for port 53 and observe what is happening at the packet level.```
sudo tcpdump -n -nn -tttt -i eth0 port 53
```
172.16.254.1 is my D-Link wireless router, which my Comcast modem is connected to. It's my default gateway. I added it as the secondary DNS, in hopes that if Hermes is down, it will still allow my Internet to work. This seems to work, when I shut Hermes down, my Internet speed is very slow, but DNS lookups still work. However, if this is a bad idea, bad practice, or the culprit, I can turn it off.

To that end, what is the command to view the assigned DNS servers on a Linux workstation? The command 'ifconfig' does not show me that. Is /etc/resolv.conf the only place?

I pinged Hermes while running 'sudo tcpdump -n -nn -tttt -i eth0 port 53' and this is one of the results:
```
2012-10-09 13:44:13.507941 IP 172.16.254.10.32871 > 172.16.254.1.53: 5167+ PTR? 132.65.215.67.in-addr.arpa. (44)
```

That looks like a very useful command, I'm saving that one. :)

---

### Post by Doug S on 2012-10-09
I would have expected it to go to 172.16.254.5 first, but it doesn't.
I missed this before, for this line:```
dns-nameservers 172.16.254.5, 172.16.254.1
```take out the comma (and then re-boot or re-start networking (which I can not recall how at the moment)).
Yes, /etc/resolv.conf is the only way I know to list the DNS servers. What does it say before and after the change I suggested above?
 
I'm not sure about 172.16.254.1 as your secondary DNS, I suppose it depends on your router.

---

### Post by jlacroix on 2012-10-09
> **Doug S said:**
> I would have expected it to go to 172.16.254.5 first, but it doesn't.
I missed this before, for this line:```
dns-nameservers 172.16.254.5, 172.16.254.1
```take out the comma (and then re-boot or re-start networking (which I can not recall how at the moment)).
Yes, /etc/resolv.conf is the only way I know to list the DNS servers. What does it say before and after the change I suggested above?
 
I'm not sure about 172.16.254.1 as your secondary DNS, I suppose it depends on your router.
You're brilliant! It was the comma in dns-nameservers that caused the issue. That made 172.16.254.5 an invalid address, so it fell back to 172.16.254.1. Now everything appears to be working.

Thanks again! :)

---

