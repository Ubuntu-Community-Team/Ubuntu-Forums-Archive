---
title: "Host Only Networking Virtual Box Help"
date: 2012-08-21
forum: Virtualisation
---

### Post by noorez on 2012-08-21
Setup:

Host: Mac OSX
IPv4: 192.168.56.1
DHCP: 192.168.52.100
Server Mask: 255.255.255.0
Address Bound: 192.168.52.101
Adress Bound: 192.168.52.110

Guest1: 
eth0: bridged to en0
IPv4: 192.168.1.76
Mask: 255.255.255.0

eth1: host network
192.168.52.101
255.255.255.0

Guest2:
eth0: host network
192.168.52.102
255.255.255.0

I can ssh between the guests but I cannot ssh between the hosts and the guest. Have I misconfigured something?

---

### Post by TheFu on 2012-08-22
I'm surprised that nobody has responded.  I've never used host-only NAT, so I have no idea what the answer is. I don't use OSX either, but on Linux, you might take a look at the OS routes and see if the virtual interfaces really are connected the way you think with the correct routes.
**  route**
should be the CLI command.  You might want to check the routes from the hostOS and each clientOS.  To me, it looks like both the guestOSes are on the same subnet, so those are routed by vbox. 192.168.52.x

What is "en0"?

---

### Post by noorez on 2012-08-22
en0 is the Mac Ethernet device
The IP address I gave for the host was the host only adaptor. The IP address for the en0 device is 192.168.1.60. I am not using NAT anywhere...
I will attach the route table soon.

---

