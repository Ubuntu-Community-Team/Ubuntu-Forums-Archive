---
title: "ubuntu server + browser question"
date: 2007-07-10
forum: Server Platforms
---

### Post by md5hash on 2007-07-10
how can i access my server from the browser using its hostname and not the ip address?
 server has a static ip address and LAMP installed.

any idea?

---

### Post by DalekClock on 2007-07-10
Have you tried enabling Remote Desktop on the server and accessing it via the Terminal Server client on the desktop?

---

### Post by primski on 2007-07-10
If you have a registered domain that shouldn't be a problem.

If you have a dns server, you could set up anoter instance serving only to LAN computers, and define a domain there.

Other than that, i think, your only option is to enter its hostname to the client's hostname file.

---

### Post by az on 2007-07-10
The web server does not do DNS.  You need a DNS server to do DNS.  You can install a DNS server on the same machine as the web server.  The point is LAMP has nothing to do with DNS.

---

### Post by md5hash on 2007-07-10
hi all just an addtional info, my LAMP server is for our local intranet apps only

---

### Post by Mr. C. on 2007-07-11
You need a hostname to IP translation service.  Options are, in order of difficulty (setup, and more importantly, someone explaining how to resolve misconfigurations )

[LIST=1]
[*]/etc/hosts
[*]dnsmasq
[*]bind/named
[*]winbind
[/LIST]

MrC

---

### Post by md5hash on 2007-07-11
what will i do?

---

### Post by Mr. C. on 2007-07-11
I suppose you'll have to tell us what you want to do!

Configure hosts files for your systems.  Edit /etc/hosts on each system, and add entries for your machines.  Entries look like:

```
192.168.0.11          host1
192.168.0.23          host2
```

where you configure your own hostname / IP paris.

MrC

---

### Post by md5hash on 2007-07-11
do i need to edit the /etc/network/interfaces too? server should have static ip?

---

### Post by Mr. C. on 2007-07-11
You said the server has a static IP address.  No need to change.

No need to change /etc/network/interfaces.

MrC

---

### Post by md5hash on 2007-07-11
i read something [https://help.ubuntu.com/ubuntu/serverguide/C/network-configuration.html](https://help.ubuntu.com/ubuntu/serverguide/C/network-configuration.html) you need to change it ip is static

---

### Post by Mr. C. on 2007-07-11
I'm not sure what your point is.  You said:

> **md5hash said:**
> 
 server has a static ip address and LAMP installed.


Please be more clear, and get off the lazy-ship if you want help.

MrC

---

### Post by md5hash on 2007-07-11
i added my hostname/ip to our dns server.. 
i think i still need to configure my /etc/networking/interfaces

here is the current content

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 130.10.1.15
        netmask 255.255.0.0
        network ??? help
        broadcast ??? help
        gateway ??? (is this where i will place my dns ip address?
```

---

### Post by jefffq on 2007-07-11
Why do you think you need to edit that? All you're doing is resolving an IP addres to a name.

And no, a gateway has nothing to do with DNS. That's where you would put the IP to a firewall/router type device that is the 'gateway' out of a private network.

If you're unclear about this file, just try googling the filename and you'll no doubt find many manuals and articles explaining it's every nuance.

---

