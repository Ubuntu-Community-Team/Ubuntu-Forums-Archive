---
title: "1st steps in understanding DNS: dnsmaq. Name resolution not working: unknown host"
date: 2011-07-01
forum: Server Platforms
---

### Post by LtPitt on 2011-07-01
Hi everybody...

I'm studying DNS and I've decided to try and understand dnsmasq before getting deeper with BIND.

Installation and configuration was really a snap (imho is great for sbs installation) but it doesn't work as I expect.

Here's my config file:

```
addn-hosts=/etc/dnshosts
no-hosts
server=/dns/192.168.1.128
domain=home.local
interface=eth0
expand-hosts
dhcp-range=192.168.1.10,192.168.1.20,255.255.255.0,48h

# Router
dhcp-option=3,192.168.1.1

# set netbios-over-TCP/IP nameserver(s) aka WINS server(s)
dhcp-option=44,192.168.1.128

# netbios datagram distribution server
dhcp-option=45,192.168.1.128
dhcp-option=46,8 # netbios node type
dhcp-option=47 # empty netbios scope

# DNS
dhcp-option=6,192.168.1.128
dhcp-option=15,home.local

#dhcp-lease-max=500
mx-host=dns.home.local,50
mx-target=dns.home.local
localmx
log-queries
log-dhcp
strict-order
dhcp-authoritative
```

and here's my small /etc/dnshosts file:

```
192.168.1.128 dns home.local
192.168.1.1 router
```

ip address are assigned correctly...

when I try nslookup from a client I get:

> nslookup dns

localhost:~ pitto$ nslookup dns
Server:         192.168.1.128
Address:        192.168.1.128#53

Name:   dns
Address: 192.168.1.128

Perfect.

So I do a ping

```
ping dns
```

WHAM

```
unknown host
```

O_O

why?

---

### Post by LtPitt on 2011-07-01
None knows why but rebooting the client solved the problem :)

Excuse me for wasting everyone's time.

---

### Post by collisionystm on 2011-07-01
Is your client a windows or linux box?

If windows you should have performed 

ipconfig /release

ipconfig /renew

Then attempted to PING

However,

I think bind9 and dhcpd server are much easier :p

dnsmasq just seems like such a hack job.

---

### Post by LtPitt on 2011-07-01
You were right indeed! :D

Really? :O
Now that this 1st setup is up and running I'll start studying "serious" packages :)

But it looks so big and complex...
I hope I'll survive :P :)

---

### Post by collisionystm on 2011-07-01
Nah, bind9 is very easy!!!

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

---

