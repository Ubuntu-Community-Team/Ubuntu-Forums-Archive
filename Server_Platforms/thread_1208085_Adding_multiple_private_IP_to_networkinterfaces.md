---
title: "Adding multiple private IP to network/interfaces"
date: 2009-07-08
forum: Server Platforms
---

### Post by wxman on 2009-07-08
I'm trying to add multiple private IP's to my /etc/network/interfaces. I'm running 8.04 server 64 bit with two NIC's. My /etc/network/interfaces looks like this:
```
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.31.202
 gateway 192.168.31.1
 netmask 255.255.255.0
 network 192.168.31.0
 broadcast 192.168.31.255
 dns-nameservers 71.243.0.12 71.250.0.12
 dns-search tlthost.net
 
auto eth0:0
iface eth0:0 inet static
  address 192.168.31.203
  netmask 255.255.255.0
auto eth0:1
iface eth0:1 inet static
  address 192.168.31.203
  netmask 255.255.255.0

# The secondary network interface connected by a crossover cable on the other server
auto eth1
iface eth1 inet static
 address 192.168.0.202
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
```
This keeps failing on me when I restart:
```
 * Reconfiguring network interfaces...                                                                                             SIOCSIFADDR: File exists
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFNETMASK: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Failed to bring up eth0:1.

```
After a restart, and the failure, I can get the 192.168.31.203 address but not the 192.168.31.204. I've Googled this till I have a headache, but no answers work. I'm hoping someone here sees what I'm doing wrong.

---

### Post by dutchman72 on 2009-07-08
204? I noticed you have .203 listed for both of the sub addresses on eth0. This will be the cause of the error message, they do need to be separate address to be assigned.

---

### Post by wxman on 2009-07-09
> **dutchman72 said:**
> 204? I noticed you have .203 listed for both of the sub addresses on eth0. This will be the cause of the error message, they do need to be separate address to be assigned.

Actually that was a mistake in pasting it here. it's really .204.

Is there a way to see if the addresses are assigned somewhere else? I've used ifconfig, and looked everywhere else I can see. I only have eth0 and eth1.

---

