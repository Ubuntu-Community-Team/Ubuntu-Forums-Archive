---
title: "SAMBA4 KDC issue, cant resolve realm"
date: 2013-07-12
forum: Server Platforms
---

### Post by BloodyIron on 2013-07-12
So I've provisioned a new domain with SAMBA4 and now I'm testing it

In /etc/hosts domain.local points to the IP of the host

In /etc/network/interfaces dns-nameservers only declares the IP of the host, dns-realm is set to domain.local, same for dns-search

So I do:

```
kinit administrator@DOMAIN.LOCAL
```

And receive:

```
kinit: Cannot resolve servers for KDC in realm "DOMAIN.LOCAL" while getting initial credentials
```

I then ping domain.local and it not only resolves but responds to pings.

I'm at a loss as to where I'm falling short here.

---

### Post by BloodyIron on 2013-07-15
bump

---

### Post by Toxic64 on 2013-08-30
yep you need to sudo that command

---

### Post by JnPson on 2013-08-31
I've had that problem too, and I found that I needed to point the servers DNS to itself. 

Nano /etc/network/interfaces

```

auto eth0
iface eth0 inet static[INDENT]address **172.16.0.2**
netmask 255.255.0.0
network 172.16.0.0
gateway 172.16.0.1
dns-nameservers **172.16.0.2** 8.8.8.8
dns-search DOMAIN.LOCAL[/INDENT]

```[INDENT]
[/INDENT]

---

### Post by meaje2 on 2014-03-17
You do realize that it is actually looking for hostanames similar to _kdc._tcp.domain.local, _kinit._tcp.domain.local etc... So of couse your pings to domain.local work the problem is most likely your dns is not getting updated with the glue reccords that the newer IPv6 services are requesting in the form of _service._tcp|_udp.doamain...  Hope this helps someone out there, I beat my head against this wall for a few hours before realizing that it was not asking for the host / domain name but a service name lookup instead.

---

