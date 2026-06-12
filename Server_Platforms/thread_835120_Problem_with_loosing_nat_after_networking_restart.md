---
title: "Problem with loosing nat after networking restart"
date: 2008-06-20
forum: Server Platforms
---

### Post by Pro_D on 2008-06-20
I have a new ubuntu server 8.04 LTS up and going.  I used ufw for firewall (my understanding is it's something of a frontend to iptables).

The problem is when I do '/etc/init.d/networking restart' I loose the ability of computers in the network to see anything outside the network.  The server itself can still ping out to the internet though it's just that the nat, or masquerade aspect is dead until I reboot.

I have searched for if there is some way (or need) to restart ufw or iptables and nothing so far.  I did manage to find the ufw script to restart ufw but that doesn't help.

---

### Post by imneo on 2008-06-20
post you /etc/network/interfaces

---

### Post by Pro_D on 2008-06-30
relevant (non remarked) lines with some remarks...

# webmin did the following line...
auto lo eth1 eth0

# The loopback network interface
iface lo inet loopback

# The primary (Internet) network interface
iface eth1 inet dhcp

# The secondary (House) network interface
iface eth0 inet static
        address         192.168.1.1
        netmask         255.255.255.0
        network         192.168.1.0
        broadcast       192.168.1.255
        gateway         192.168.1.1

eof

A bit of a delay in the reply, ended up moving onto other things for a while...

---

### Post by windependence on 2008-06-30
Your IP address cannot be the same as your gateway. Is this a gateway box? Do you have a router in front of this? How is this connected to the inernet?

-Tim

---

### Post by Pro_D on 2008-07-03
It is acting as a gateway.  It is directly connected to a dsl modem which is acting as a nat router.  The modem is a lousy bit of hardware which gets overwhelmed with medium activity on our network and I am hoping I may find a way to bypass it's nat functionality for a direct (more or less) connection to the internet.... but that's another topic.

I tried removing (well remarking) the gateway item in the house network connection, reset the network (/etc/init.d/networking restart) and it works just dandy.

Thanks much, problem solved.

---

